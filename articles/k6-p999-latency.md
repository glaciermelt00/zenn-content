---
title: "k6 + Prometheus + Grafana で p99.9 レイテンシデータを計測・可視化する方法"
emoji: "😸"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["k6", "performance", "latency", "Grafana", "Prometheus"]
published: true
---

# 背景

[こちらの記事](https://zenn.dev/nyama39/articles/3ef0d951e2aa30)では、k6 + Prometheus + Grafana でパフォーマンス計測・可視化を紹介していましたが、p99.9 レイテンシデータは表示されていませんでした。

本記事では、k6 で p99.9 レイテンシデータを表示する方法を紹介します。

# k6 で p99.9 レイテンシデータを取得する

`compose.yml` の `k6` サービスに環境変数 `K6_PROMETHEUS_RW_TREND_STATS` を追加します。

```diff yml:compose.yml
 services:
   k6:
     image: grafana/k6:0.49.0
     ports:
       - "6565:6565"
     volumes:
       - type: bind
         source: "./scripts"
         target: "/scripts"
     environment:
       - K6_PROMETHEUS_RW_SERVER_URL=http://prometheus:9090/api/v1/write
+      - K6_PROMETHEUS_RW_TREND_STATS=p(95),p(99),p(99.9),avg,min,max
     networks:
       - k6-prometheus
```

これを指定することで、 p99.9 レイテンシデータを k6 で取得できます。

# Grafana ダッシュボードで p99.9 レイテンシデータを表示する

[k6 Prometheus Dashboard](https://grafana.com/grafana/dashboards/19665-k6-prometheus/)を使用している場合、デフォルトで p99.9 レイテンシデータを表示することが可能です。

# おまけ：　 p95, p99, p99.9 のレイテンシデータを比較するグラフを表示する

上記のダッシュボードでは、p99.9 レイテンシに関するデータのみが表示されますが、p95, p99, p99.9 のレイテンシデータを比較するグラフを表示することも可能です。
以下の手順で行います。

1. 上記のダッシュボードの JSON ファイルを別名でコピーする
2. コピーした JSON ファイルを開く
3. `panels` 配列に以下のデータを追加して保存

```json
{
  "id": 99,
  "type": "timeseries",
  "title": "Latency Quantiles (p95, p99, p99.9)",
  "datasource": { "type": "prometheus", "uid": "${DS_PROMETHEUS}" },
  "gridPos": { "h": 8, "w": 12, "x": 0, "y": 48 },
  "fieldConfig": {
    "defaults": {
      "unit": "s",
      "custom": { "lineWidth": 2, "showPoints": "auto" }
    }
  },
  "options": {
    "legend": { "displayMode": "list", "placement": "bottom" },
    "tooltip": { "mode": "multi" }
  },
  "targets": [
    {
      "expr": "avg(k6_http_req_duration_p95{testid=~\"$testid\"})",
      "legendFormat": "p95",
      "refId": "A",
      "instant": false,
      "range": true
    },
    {
      "expr": "avg(k6_http_req_duration_p99{testid=~\"$testid\"})",
      "legendFormat": "p99",
      "refId": "B",
      "instant": false,
      "range": true
    },
    {
      "expr": "avg(k6_http_req_duration_p999{testid=~\"$testid\"})",
      "legendFormat": "p99.9",
      "refId": "C",
      "instant": false,
      "range": true
    }
  ]
}
```

4. JSON ファイルを Grafana ダッシュボードにインポートする

この作業により、以下のようなグラフを追加することができます。

![](https://storage.googleapis.com/zenn-user-upload/dced6c780ecf-20250525.png)

# メモ

k6 でサクッとパフォーマンス計測ができることがわかりました。

ユースケースの所管としては：

- 初期導入: ローカル実行で十分
- 定期実行をする場合: 仕組みを整える (GitHub Actions の schedule イベントなど)
- 複数のチームメンバーで運用する場合: [Grafana Cloud k6](https://grafana.com/ja/products/cloud/k6/) を利用する

GitHub Actions の schedule イベントは、是非導入したいですね。
