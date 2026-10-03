---
title: "Prisma で Postgres の RLS を入れたら、公式レシピ通りでもトランザクションの中で効かなかった話"
emoji: "🔒"
type: "tech"
topics: ["postgresql", "prisma", "rls", "typescript", "sre"]
published: false
---

マルチテナントのサービスで、Postgres の Row Level Security（RLS）を Prisma から使う話です。公式ドキュメントのレシピ通りに書いたのに、対話型トランザクションの中で効いたり効かなかったりした原因と、直し方、効いていることをどう確かめたかをまとめます。

対象は「Prisma は使っている、RLS はこれから」の人です。コードは要点だけに削っているので、そのまま動く保証はありません。

## なぜ RLS を入れたか

アプリ側で `where: { tenantId }` を毎クエリに付ける方式は、1 か所の漏れで他テナントのデータが見えます。数十テーブルあると、レビューで全部を追い切るのは無理です。DB 側に「テナントの文脈が無ければ 1 行も返さない」を持たせたくて RLS にしました。

```sql
ALTER TABLE orders ENABLE ROW LEVEL SECURITY;
ALTER TABLE orders FORCE ROW LEVEL SECURITY;  -- テーブルの所有者にも適用

CREATE POLICY tenant_isolation ON orders
  USING (tenant_id = current_setting('app.tenant_id', true)::uuid);
```

ポイントは `FORCE`。これが無いと、テーブルの所有者ロール（マイグレーションを流すロールと同じことが多い）にはポリシーが効きません。

## 公式レシピ

Prisma のドキュメントにある方法は、Client extensions で全クエリを包み、`SET` とクエリをバッチトランザクションにする形です。

```ts
const prisma = new PrismaClient().$extends({
  query: {
    $allOperations({ args, query }) {
      const tenantId = getTenantIdFromContext();
      return prisma.$transaction([
        prisma.$executeRaw`SELECT set_config('app.tenant_id', ${tenantId}, TRUE)`,
        query(args),
      ]);
    },
  },
});
```

`set_config(..., TRUE)` の第 3 引数が `is_local` で、トランザクションが終わると設定が消えます。1 クエリごとに `[SET, query]` を 1 つのトランザクションにすることで、設定が他のリクエストに漏れないようにしています。

単発のクエリでは、これで動きます。

## 罠 1: 対話型トランザクションの中で効かない

問題は、業務ロジックの大半が対話型トランザクションの中にあることです。

```ts
await prisma.$transaction(async (tx) => {
  const order = await tx.order.create({ ... });
  await tx.stock.update({ ... });
});
```

この `tx` に対して上の拡張が動くと、各クエリは `[SET, query]` のバッチトランザクションとして実行されます。つまり **外側の `$transaction` とは別のトランザクションで走る**。テナントの文脈は付きますが、`order.create` と `stock.update` が同じトランザクションにいる保証が無くなり、原子性が壊れます。

さらに、拡張がどのタイミングでどのクライアントに対して動くかで挙動が変わるので、「効いたり効かなかったり」に見えます。テストで通って本番でだけ変な動きをする、が一番怖い形です。

## 直し方: トランザクションの先頭で 1 回だけ SET LOCAL

「毎クエリで SET を打つ」発想をやめて、**トランザクションの入口で 1 回だけ** `SET LOCAL` を打ちます。以降のクエリは同じトランザクションの中で走るので、設定は全部に効きます。

対話型トランザクションの中にいるかどうかは、`AsyncLocalStorage` にマーカーを置いて判定しました。

```ts
import { AsyncLocalStorage } from "node:async_hooks";

const txContext = new AsyncLocalStorage<{ tenantId: string; applied: boolean }>();

export async function withTenantTx<T>(
  tenantId: string,
  fn: (tx: Prisma.TransactionClient) => Promise<T>,
) {
  return prisma.$transaction(async (tx) => {
    await tx.$executeRaw`SELECT set_config('app.tenant_id', ${tenantId}, TRUE)`;
    return txContext.run({ tenantId, applied: true }, () => fn(tx));
  });
}

const prisma = new PrismaClient().$extends({
  query: {
    $allOperations({ args, query }) {
      const ctx = txContext.getStore();
      if (ctx?.applied) {
        return query(args);            // tx の中。SET は入口で済んでいる
      }
      const tenantId = getTenantIdFromContext();
      return prisma.$transaction([    // tx の外。従来どおり 1 クエリ 1 tx
        prisma.$executeRaw`SELECT set_config('app.tenant_id', ${tenantId}, TRUE)`,
        query(args),
      ]);
    },
  },
});
```

要点は 2 つです。

- トランザクションの中では、拡張は何もしない（入口で打った `SET LOCAL` が全クエリに効く）
- トランザクションの外では、従来どおり 1 クエリ 1 トランザクションで包む

`SET LOCAL` はトランザクションが終わると消えるので、コネクションプールで次のリクエストに漏れることもありません。

## 罠 2: current_setting は未設定で NULL を返す

もう 1 つ、静かに効かなくなる罠があります。

```sql
current_setting('app.tenant_id', true)
```

第 2 引数 `missing_ok = true` のとき、未設定なら **NULL** が返ります。空文字ではありません。ポリシーで `= ''` と比べていると、永遠に一致しません。

これは逆に使えます。`tenant_id = NULL::uuid` は常に偽なので、**文脈が無ければ 1 行も返らない（fail closed）** になります。「効いていないときに全件見える」ではなく「効いていないときに何も見えない」側に倒れるのは、RLS では正しい向きです。

ただし、fail closed は「壊れた時に静か」でもあります。次の節の検知が要る理由です。

## 効いていることを、どう確かめたか

RLS は「入れた」と「効いている」の間に距離があります。3 段で見ています。

### 1. 静的: ポリシーの本数を数える

`pg_policies` を引いて、ポリシーの本数と `FORCE` が付いているテーブルの本数が、対象テーブル数と一致するかをマイグレーションのたびに数えます。数十テーブルあると、1 つ抜けていても見た目では分かりません。

```sql
SELECT count(*) FROM pg_policies WHERE schemaname = 'public';
SELECT count(*) FROM pg_class c
  JOIN pg_namespace n ON n.oid = c.relnamespace
 WHERE n.nspname = 'public' AND c.relkind = 'r' AND c.relforcerowsecurity;
```

### 2. 実行前: 使い捨ての DB で組み合わせを回す

ローカルの使い捨て DB で、「文脈なし / 別テナント / 同テナント」×「トランザクションの中 / 外」の組み合わせを回し、**文脈なしと別テナントが必ず 0 件になる**ことを見ます。ここで罠 1 と罠 2 の両方が引っかかります。

### 3. 実行中: 「文脈なしでクエリが走った回数」を数える

本番で見たいのは「件数が 0 になった」ではありません。小さいテナントや休眠テーブルでは、正常でも 0 件なので、件数にしきい値を持たせると鳴り続けます。

代わりに、トランザクションの入口で `current_setting` が NULL のままクエリが走った回数を数えます。これは 0 以外が全部異常なので、テナントの大きさや時間帯に依存しません。この部分はログからカスタムメトリクスに起こす形で設計していて、観測期間に入る前に入れる予定です（この記事の時点では未実装です）。

## 本番への切り替え方

RLS は「有効にした瞬間に全部の読み取りが変わる」ので、戻し方を先に決めました。

- ロールを 2 本にする。アプリ用は `NOBYPASSRLS`、管理用（マイグレーション）は `BYPASSRLS`
- 切り替えは DDL ではなく **接続文字列の差し替え**。パラメータストアの `DATABASE_URL` をアプリ用ロールに変えると発効し、戻すのは元の文字列に戻す 1 手
- `GRANT ... ON ALL TABLES IN SCHEMA` は、所有者が違うテーブルが 1 つ混ざると文ごとロールバックするので、所有テーブルに限定した `DO` ループにした
- dev 環境で数日、通常運用のまま観測してから本番

「切り替え」と「戻し」を同時に設計しておくと、本番で手が止まりません。

## まとめ

- 公式レシピの `[SET, query]` バッチは、対話型トランザクションの中では別トランザクションになり、原子性が壊れる
- 直し方は、トランザクションの入口で 1 回だけ `SET LOCAL`。中にいるかどうかは `AsyncLocalStorage` で判定
- `current_setting(name, true)` は未設定で NULL。`= ''` は永遠に一致しない。NULL を fail closed に使う
- 「入れた」と「効いている」は別。本数を数え、使い捨て DB で組み合わせを回し、本番では「文脈なしで走った回数」を見る
- 切り替えは接続文字列で。戻しは 1 手

公式ドキュメントは正しいです。前提にしている接続モデルが、対話型トランザクションと違うだけでした。公式通りに書いて壊れたときは、公式が前提にしているものを疑うのが早かった、という話でもあります。
