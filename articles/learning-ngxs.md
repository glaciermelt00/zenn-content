---
title: "NGXSを学ぶ"
emoji: "⛳"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false
---

https://www.ngxs.io/

NGXSは、Angularのための状態管理パターン＋ライブラリです。
アプリケーションの状態を管理する単一のソースとして機能し、予測可能な状態変化のためのシンプルなルールを提供します。

NGXSは、ReduxやNgRxなどのライブラリで一般的に実装されているCQRSパターンをモデルとしています。
しかし、クラスやデコレーターなどの最新のTypeScript機能を使用することで、定型的な表現を減らしています。


# Introduction

NGXSには4つの大きなコンセプトがあります。

- Store: グローバルステートコンテナ、アクションディスパッチャ、セレクタ
- Action: 実行するアクションと、それに関連するメタデータを記述するクラス
- State: 状態を定義するクラス
- Selecter: Stateはselectorをスライスする

これらの概念により、アクションを発信するコンポーネントから、アクションに反応するストア、そしてステートセレクトを介してコンポーネントに戻る、循環型の制御フローが形成されます。


# Store

Storeは、

- ステートコンテナがリッスンするアクションをディスパッチし、
- グローバルステートからデータスライスを選択する方法を提供する、

グローバルステートマネージャーです。



---------------------------------------------------------------

なんともわかりづらい。
英語の公式ドキュメントは、どこか読みにくい。いい読み方があるのかな。。。

https://nextbeat-external.atlassian.net/wiki/spaces/DEV/pages/1625751900/7#ngxs

こちらで共有されている、

https://medium.com/nextbeat-engineering/angular%E3%81%AE%E7%8A%B6%E6%85%8B%E7%AE%A1%E7%90%86%E3%83%A9%E3%82%A4%E3%83%96%E3%83%A9%E3%83%AA-ngxs-%E3%81%AB%E5%85%A5%E9%96%80%E3%81%99%E3%82%8B-d40b3591b5a6

ここの下記記事から始めた方が良さそう。

https://medium.com/nextbeat-engineering/angular%E3%81%AE%E7%8A%B6%E6%85%8B%E7%AE%A1%E7%90%86%E3%83%A9%E3%82%A4%E3%83%96%E3%83%A9%E3%83%AA-ngxs-%E3%81%AB%E5%85%A5%E9%96%80%E3%81%99%E3%82%8B-d40b3591b5a6


## NGXSのインストール

ngxsとプラグインをインストールする。

```
$ npm install @ngxs/store --save

added 7 packages, and audited 8 packages in 11s

1 package is looking for funding
  run `npm fund` for details

found 0 vulnerabilities
jo.harada@: ~/learning/ngxs
$ npm install @ngxs/store@dev --save

changed 1 package, and audited 8 packages in 4s

1 package is looking for funding
  run `npm fund` for details

found 0 vulnerabilities
jo.harada@: ~/learning/ngxs
$ npm install @ngxs/logger-plugin@dev --save

added 2 packages, and audited 10 packages in 8s

2 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

分からんリスト

- デコレータって何
- ハンドリングって何
- dispatchって何

NGXSではStateContextを用いることでStateクラス内で状態更新ロジックを書くことができます。
NgRxのように、状態更新ロジックをReducerに切り出して記述しなくてもよくなります。


