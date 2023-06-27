---
title: "メモ"
---

# コマンド系

- バージョン確認
    
    ```bash
    $ go version
    ```
    
- 依存性追跡の有効化
    
    ```bash
    $ go mod init <prefix>/<descriptive-text>
    ```
    
    - prefix: モジュールを部分的に説明する文字列
    - descriptive-text: プロジェクト名
        - https://go.dev/doc/modules/managing-dependencies#naming_module
- コードの実行
    
    ```bash
    $ go run .
    ```
    
- 新規モジュールの要件・サムの追加
    
    ```bash
    $ go mod tidy
    ```
    

# コーディング系

- `package main`
    - `main` パッケージの宣言
- `import "fmt"`
    - `fmt` パッケージのインポート
- 複数パッケージのインポート
    
    ```go
    import {
      "fmt"
    
      "rsc.io/quote"
    }
    ```
    
- `func main() { ... }`
    - `main` 関数の実装
- `func Hello(name string) string { ... }`
    - `Hello` 関数の実装
        - 引数：　`string` 型の `name` パラメータ
        - 返り値の型：　`string` 型
- `fmt.Println()`
    - コンソールにメッセージを出力
- `fmt.Sprintf("... %v ...", name)`
    - 第一引数：　フォーマット文字列
    - 第二引数：　パラメータ：　`%v` フォーマット動詞に置き換える
- `quote.Go()`
    - Go のことわざを取得
- `message := ...`
    - 変数の宣言・初期化
    - 型：　右側の値により決定される
- `errors.New("...")`
    - エラーを返す
    - 引数：　出力したいテキスト
- `if name == ""`
    - if 文
    - 比較演算子 `==`
- `nil`
    - エラーがないことを意味する
    - エラーハンドリングの際、関数が成功する場合に渡す
- `log.SetPrefix("...")`
    - ロガー出力のプレフィックスを設定する
- `log.SetFlags(0)`
    - ログメッセージの先頭から、タイムスタンプ・ソースファイル情報・行番号を除外する
- `message, err := greetings.Hello("")`
    - `greetings.Hello("")` の返り値のエラーとして、 `err` で受け取れるようにする
- `log.Fatal(err)`
    - `err` を出力して、プログラムを停止する
- `func randomFormat() string { ... }`
    - 関数名が小文字で始まる場合、独自のパッケージ内からしかアクセスできない
        - つまり、エクスポートされない
- `for _, name := range names { ... }`
    - スライスから value を取り出して for ループを回す
- `messages[name] = message`
    - マップでキーと値を関連づける
- `names := []string{"A", "B", "C"}`
    - スライスの変数を作成

# パッケージ系

- `fmt` パッケージ
    - https://pkg.go.dev/fmt
    - `Println` 関数：　オペランドのデフォルト形式を使用してフォーマットし、標準出力に書き込む
        - オペランドの間には常にスペースが追加され、改行が追加される
        - 書き込まれたバイト数と、発生した書き込みエラーを返す
    - `Sprintf` 関数：　フォーマット指定子に従ってフォーマットし、結果を返す
- `quote` パッケージ
    - https://pkg.go.dev/rsc.io/quote/v4#Go
    - `Go` 関数：　Go のことわざを返す
        
        ```bash
        Don't communicate by sharing memory, share memory by communicating.
        ```
        
- `errors` パッケージ
    - https://pkg.go.dev/errors
    - `New` 関数：　エラーを返す：　与えられたテキストとしてフォーマットする
        - それぞれの`New` の呼び出しは個別のエラー値を返す：　テキストが同一の場合でも
- `log` パッケージ
    - https://pkg.go.dev/log
    - `SetPrefix` 関数：　出力のプレフィックスを設定する：　標準ロガーで
    - `SetFlags` 関数：　ロガーの出力フラグを設定する
        - フラグビットは Ldate, Ltime など
    - `Fatal` 関数：　`Print()` の後に `os.Exit(1)` を呼び出すのと同等
- `math/rand` パッケージ
    - https://pkg.go.dev/math/rand
    - `Intn` 関数：　`int` として、非負の擬似ランダムな数を返す：　デフォルトの Source から半開区間 `[0, n)` で
        - n が 0以下の場合、パニックになる

# モジュール系

- ローカルのモジュールを適用する
    - `go mod edit -replace` を使う
        
        ```go
        $ go mod edit -replace example.com/greetings=../greetings
        ```
        
        - `../greetings` ディレクトリに存在する `[example.com/greetings](http://example.com/greetings)` モジュールを使用するため、依存関係を指定する
        - `go.mod` ファイルに `replace` ディレクティブが追加される
            
            ```go
            replace example.com/greetings => ../greetings
            ```
            
    - `go mod tidy` を使う
        
        ```bash
        $ go mod tidy
        go: found example.com/greetings in example.com/greetings v0.0.0-00010101000000-000000000000
        ```
        
        - `go.mod` ファイルに `require` ディレクティブが追加される
            
            ```go
            require example.com/greetings v0.0.0-00010101000000-000000000000
            ```
            

# 型

- スライス
    - `[]string`
    - 配列に似ている
    - 要素の追加・削除で、サイズが動的に変化する
- マップ
    - `map[KeyType]ValueType`
    - 初期化：　make 関数を使う：　`make(map[string]int)`

