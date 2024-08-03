---
title: "ORM: gorm x PostgreSQL で JSON データを読み書きする方法"
---

# 背景

- PostgreSQL で JSON データを読み書きするケースがあると思います。
- 公式ドキュメントを参考にして Scanner / Valuer を書いてもエラーが発生するケースに出会したので、回避方法について備忘録的にメモします。

# 公式ドキュメントの Scanner / Valuer の実装

- [公式ドキュメント](https://gorm.io/docs/data_types.html#Implements-Customized-Data-Type)では、下記のサンプルコードが掲載されている。

```go
type JSON json.RawMessage

// Scan scan value into Jsonb, implements sql.Scanner interface
func (j *JSON) Scan(value interface{}) error {
  bytes, ok := value.([]byte)
  if !ok {
    return errors.New(fmt.Sprint("Failed to unmarshal JSONB value:", value))
  }

  result := json.RawMessage{}
  err := json.Unmarshal(bytes, &result)
  *j = JSON(result)
  return err
}

// Value return json value, implement driver.Valuer interface
func (j JSON) Value() (driver.Value, error) {
  if len(j) == 0 {
    return nil, nil
  }
  return json.RawMessage(j).MarshalJSON()
}
```

- 上記では `json.RawMessage` 型の `JSON` 型を定義し、それぞれ `Scan` / `Value` メソッドを定義しています。

# カスタムデータ型の Scanner / Valuer 実装

- 上記を参考にして、 カスタムデータ型として `Plan` 型を定義し、それに相当する `Scan` / `Value` メソッドを定義してみましょう。
- `meta_data` カラムを PostgreSQL の `jsonb` 型として想定します。

```go:model.go
import (
	"time"
)

type Plan struct {
  ID        int
  Title     string
  MetaData  MetaData   // JSON データ
  CreatedAt time.Time
  UpdatedAt time.Time
}

type MetaData struct {
  Memo string
}
```

- `Scan` / `Value` メソッドを定義します。

```go:model.go
import (
  "database/sql/driver"
  "encoding/json"
  "errors"
  "fmt"
)

// MetaData 型のカスタムスキャンメソッドを定義
func (md *MetaData) Scan(value interface{}) error {
	byteValue, ok := value.([]byte)
	if !ok {
		return errors.New(fmt.Sprint("Failed to unmarshal JSONB value:", value))
	}

	// バイトデータをMetaData構造体にデコード
	return json.Unmarshal(byteValue, &md)
}

// カスタムバリューメソッドも追加する
func (md MetaData) Value() (driver.Value, error) {
	return json.Marshal(md)
}
```

- これで、`Plan` 型の `MetaData` フィールドに JSON データを読み書きするためのメソッドが定義されました。
- 一見、上記で問題なさそうに見えますが、実際にはエラーが発生します。

# エラーの内容

- 上記の場合、 `Scan` メソッド（読み込み）は問題なく動作します。
- しかし、 `Value` メソッド（書き込み）でエラーが発生します。

```bash
ERROR: invalid input syntax for type json (SQLSTATE 22P02)
INSERT INTO "plans" ("title","meta_data","created_at","updated_at") VALUES ('title_1','{"memo":"memo_1"}','2024-08-01 10:00:00','2024-08-01 10:00:00') RETURNING "id"
```

- (ちなみに、エラーログに出力された SQL を直接実行すると、正常に INSERT されます。)

# 解決方法

- `Plan` 型の `MetaData` フィールドを `MetaData` 型から `datatypes.JSON` 型に変更します。

```go:model.go
import (
	"time"

  "gorm.io/datatypes"
)

type Plan struct {
  ID        int
  Title     string
  //MetaData  MetaData       // Before
  MetaData  datatypes.JSON   // After
  CreatedAt time.Time
  UpdatedAt time.Time
}

type MetaData struct {
  Memo string
}
```

# 原因

- おそらく gorm 側の処理と PostgreSQL 側の処理がうまくマッチしていないため、エラーが発生していると思われます。

# 参考ドキュメント

- [GORM - Customize Data Types](https://gorm.io/docs/data_types.html)
- [Go - datatypes](https://pkg.go.dev/gorm.io/datatypes@v1.2.1)
