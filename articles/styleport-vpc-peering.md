---
title: "複数アカウントで同じ VPC CIDR ブロックを使っている環境下で VPC peering を実現してみた"
emoji: "💭"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["AWS", "VPC", "Peering", "CIDR", "セカンダリ"]
published: false
publication_name: "styleport"
---

## はじめに

こんにちは、スタイルポートで SRE を担当している glaciermelt です。

AWS で複数アカウントを運用していると、VPC 間の通信が必要になることがあります。通常は VPC peering で簡単に解決できますが、**同じ CIDR ブロックを使用している VPC 同士では peering ができない**という制約があります。

本記事では、この制約をセカンダリ CIDR を活用して回避し、既存環境への影響を最小限に抑えながら VPC 間通信を実現した方法を紹介します。

## この記事で得られること

- 同一 CIDR ブロックを持つ VPC 間での通信を実現する方法
- セカンダリ CIDR を使った VPC peering の実装手順
- EC2 で複数のネットワークインターフェース（ENI）を使う設定方法
- 実際のルーティング設定の例

## 背景

弊社の DiSIM 事業では、現在複数の AWS アカウントを使用しております。

現状では各アカウントで複数の EC2・RDS インスタンスをそれぞれ立てているのですが、 EC2・RDS インスタンスを集約してコスト削減を図りたいと考えています。

様々な事情を踏まえて、EC2 インスタンスは各アカウントで一つのインスタンスに集約し、 RDS インスタンスは新規アカウントのものに集約することとしました。

## 課題

EC2 インスタンスは問題なく集約できたものの、問題は RDS インスタンスの集約です。

しかし、各アカウントの EC2 インスタンスを立てている VPC では同じ CIDR ブロックを使用していることが判明しました。

:::message
**VPC peering の制約**
VPC peering では、接続する VPC 間で CIDR ブロックが重複していると接続できません。これは AWS の仕様上の制限で、ルーティングの競合を防ぐためです。
:::

現在の状況は以下のとおりです。

| AWS アカウント | VPC CIDR ブロック |
| -------------- | ----------------- |
| アカウント A   | 16.8.0.0/16       |
| アカウント B   | 16.8.0.0/16       |
| アカウント C   | 16.16.0.0/16      |
| アカウント D   | 16.64.0.0/16      |

RDS を集約するためにはアカウント A ~ D で VPC を接続する (VPC peering) する必要があるのですが、 **アカウント A とアカウント B の VPC CIDR ブロックが同じ (16.8.0.0/16) であるため、VPC peering ができない** という問題が発生しました。

そのため、何らかの対策が必要となりました。

## 対策案の検討

対策としては以下のような案が考えられました。

| No  | 対策案                                                                                                             | メリット         | デメリット                                             |
| --- | ------------------------------------------------------------------------------------------------------------------ | ---------------- | ------------------------------------------------------ |
| 1   | 新規の VPC を作成し、EC2 を載せ替える                                                                              | 構成がシンプル   | 工数がかかり、複数デベ・物件に影響がまたがるリスクあり |
| 2   | VPC にセカンダリ CIDR を追加し、EC2 に追加のネットワークインターフェイスをアタッチして DB 接続用ルーティングを設定 | 構成が複雑になる | 既存構成に変更がなく、リスクが少ない                   |

今回はできるだけ既存の構成に変更を加えず、リスクを少なくすることを優先し、**対策案 2（セカンダリ CIDR の活用）** を採用しました。

## 実装方法

### ソリューションの概要

今回のキモは、 **DB 接続用にセカンダリ CIDR を使用する** ことです。

:::message
**セカンダリ CIDR とは**
VPC にはメインの CIDR ブロック以外に、追加の CIDR ブロック（セカンダリ CIDR）を関連付けることができます。これにより、既存の VPC の IP アドレス空間を拡張できます。
:::

具体的には、以下の手順で実施しました。

- ネットワーク
  - ネットワークの全体構成設計
  - VPC へセカンダリ CIDR を追加
  - セカンダリ CIDR のサブネットを用意
  - VPC Peering を作成
  - ルートテーブル設定
- EC2
  - サブネット上で DB 接続用ネットワークインターフェイス作成
  - ネットワークインターフェイスを EC2 に ホットアタッチ
  - EC2 OS ルーティング
- RDS
  - Security Group 設定

### アーキテクチャ構成

以下が実現後のアーキテクチャ図です。各アカウントの VPC にセカンダリ CIDR を追加し、それらを使って VPC peering を確立しています。

![VPC Peering アーキテクチャ図](https://storage.googleapis.com/zenn-user-upload/097dc44d2b1c-20250606.png)

ポイントは以下の通りです：

- 各アカウントの EC2 にセカンダリ CIDR のネットワークインターフェースを追加
- セカンダリ CIDR と RDS VPC 間で VPC peering を確立
- OS ルーティングで RDS への通信をセカンダリインターフェース経由に設定

### 実施内容詳細

以下、各ステップの詳細を説明します。

| カテゴリ     | 項目                                                     | 内容                                                                                                                                                                                                                                                       |
| ------------ | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ネットワーク | ネットワークの全体構成設計                               | VPC セカンダリ CIDR が既存 VPC の CIDR ブロックと重複しないように設計<br><br>アカウント A: 16.8.0.0/16 → 32.0.0.0/20<br>アカウント B: 16.8.0.0/16 → 32.0.16.0/20<br>アカウント C: 16.16.0.0/16 → 32.0.32.0/20<br>アカウント D: 16.64.0.0/16 → 32.0.48.0/20 |
|              | VPC へセカンダリ CIDR を追加                             | 各アカウントの VPC にセカンダリ CIDR を追加                                                                                                                                                                                                                |
|              | セカンダリ CIDR のサブネットを用意                       | AZ ごとに /24 程度のサブネットを用意                                                                                                                                                                                                                       |
|              | VPC Peering を作成                                       | RDS 集約用アカウントと各アカウントの VPC を接続                                                                                                                                                                                                            |
|              | ルートテーブル設定                                       | 既存ルートテーブルにルーティングとサブネットを追加                                                                                                                                                                                                         |
| EC2          | サブネット上で DB 接続用ネットワークインターフェイス作成 | セカンダリ CIDR のサブネット上で DB 接続用のネットワークインターフェイス (ENI) を作成                                                                                                                                                                      |
|              | ネットワークインターフェイスを EC2 に ホットアタッチ     | ENI を稼働中の EC2 インスタンスにホットアタッチ（インスタンスを停止せずにアタッチ）                                                                                                                                                                        |
|              | EC2 OS ルーティング                                      | OS レベルで RDS への通信をセカンダリ ENI 経由にルーティング設定                                                                                                                                                                                            |
| RDS          | Security Group 設定                                      | RDS の Security Group に、各アカウントのセカンダリ CIDR ブロックからのアクセスを許可                                                                                                                                                                       |

### 具体的な実装手順

#### EC2 のルーティング設定

EC2 の OS レベルでルーティングを設定します。

```bash
$ sudo tee /etc/systemd/network/10-ens8-routing.network > /dev/null <<'EOF'
# ens8: DB 用ポリシールーティング
[Match]
Name=ens8

[Network]
DHCP=yes

# ---------- static route on table 101 ----------
[Route]
Destination=32.0.0.0/16
Gateway=32.32.4.1
PreferredSource=32.32.4.84
Table=101
Metric=100

# ---------- policy rule ----------
[RoutingPolicyRule]
To=32.0.0.0/16
Table=101
Priority=1000
EOF
```

### 実装時の注意点とベストプラクティス

#### 注意点

1. **OS ルーティングの永続化**

   - EC2 インスタンスの再起動後もルーティング設定が維持されるよう、起動スクリプトに設定を追加

2. **パフォーマンスへの影響**

   - マルチホーミング構成では、OS レベルのルーティング処理が発生するため、わずかにレイテンシが増加する可能性がある

3. **セキュリティグループの管理**
   - 複数のネットワークインターフェースを持つ EC2 には、適切なセキュリティグループのアタッチが必要

#### ベストプラクティス

1. **段階的な移行**

   - 本番環境への適用前に、検証環境で十分なテストを実施

2. **監視の強化**

   - CloudWatch でネットワークパフォーマンスを監視
   - VPC Flow Logs を有効化して通信パターンを確認

3. **ドキュメント化**
   - ネットワーク構成図と設定内容を文書化
   - 変更履歴を記録

## まとめ

今回紹介した手法により、同じ CIDR ブロックを使用している VPC 間でも通信を実現できました。

**ポイント**

- セカンダリ CIDR を活用することで、既存の IP アドレス体系を変更せずに済む
- EC2 への追加 ENI アタッチにより、柔軟なルーティング制御が可能
- ホットアタッチ対応なので、サービス停止なしで実装可能

この手法は、レガシーシステムの段階的な統合や、M&A によるシステム統合など、様々な場面で応用できます。

今後も AWS 環境でのコスト最適化とアーキテクチャの改善を推進していきたいと考えています。

## 参考リンク

- [AWS VPC ユーザーガイド - 複数の IPv4 CIDR ブロックを VPC に関連付ける](https://docs.aws.amazon.com/ja_jp/vpc/latest/userguide/VPC_Subnets.html#vpc-resize)
- [VPC peering 接続の作成と承認](https://docs.aws.amazon.com/ja_jp/vpc/latest/peering/create-vpc-peering-connection.html)
- [Amazon EC2 の Elastic Network Interface](https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/using-eni.html)
