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
    
    - モジュールを指定して実行：　example/hello モジュールを指定
        
        ```bash
        $ go run example/hello
        ```
        
- 新規モジュールの要件・サムの追加
    
    ```bash
    $ go mod tidy
    ```
    
- 依存関係の追加
    
    ```bash
    $ go get golang.org/x/example
    go: downloading golang.org/x/example v0.0.0-20230515183114-5bec75697667
    go: added golang.org/x/example v0.0.0-20230515183114-5bec75697667
    ```
    - `golang.org/x/example` モジュールに依存関係を追加
- ワークスペースの初期化
    
    ```bash
    $ go work init ./hello
    ```
    
    - `./hello` ディレクトリを含むワークスペースを初期化
    - 以下のような `go.work` ファイルが生成される
        
        ```go
        go 1.20
        
        use ./hello
        ```
        
        - `go` ディレクティブ：　ファイルを解釈する Go のバージョンを Go に指示する
        - `use` ディレクティブ：　ビルドを実行するときに ./hello ディレクトリ内のモジュールがメインモジュールである必要があることを Go に指示する
- ワークスペースにモジュールを追加
    
    ```bash
    $ go work use ./example
    ```
    
    - `./example` モジュールをワークスペースに追加

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
- `want := regexp.MustCompile(`\b`+name+`\b`)`
    - 正規表現をコンパイルする
    - name というパターンのみマッチさせる

# パッケージ系

- `fmt` パッケージ
    - https://pkg.go.dev/fmt
    - `Println` 関数：　オペランドのデフォルト形式を使用してフォーマットし、標準出力に書き込む
        - オペランドの間には常にスペースが追加され、改行が追加される
        - 書き込まれたバイト数と、発生した書き込みエラーを返す
    - `Sprintf` 関数：　フォーマット指定子に従ってフォーマットし、結果を返す
    - `%v`：　構造体を出力するときのデフォルトフォーマットの値
    - `%q` (文字列とバイトのスライス)：　Go 構文で安全にエスケープされた二重引用符で囲まれた文字列
    - `%#q`：　バッククォートされた文字列
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
- `testing` パッケージ
    - `T` 型：　テスト状態を管理し、フォーマットされたテストログをサポートするために、テスト関数に渡される型
        - `Fatalf` 関数：　`Logf` の後に `FailNow` が続くものと同等
- `regexp` パッケージ
    - `MustCompile(str string) *Regexp` 関数：　Compile に似ているが、式を解析できない場合にパニックを起こす
        - これにより、コンパイルされた正規表現を保持するグローバル変数の安全な初期化が簡素化される
    - `MatchString` 関数：　文字列 s に正規表現パターンの一致が含まれているかどうかを報告する
- `unicode` パッケージ
    - https://pkg.go.dev/unicode
    - `ToUpper` 関数：　rune を大文字にマップする


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
            
- `go build`：　パッケージとその依存関係をコンパイルする
- `go install`：　パッケージをコンパイルしてsインストールする
- `go list -f '{{.Target}}'`：　ビルドされたパッケージの場所を表示する

# 型

- スライス
    - `[]string`
    - 配列に似ている
    - 要素の追加・削除で、サイズが動的に変化する
    - スライスの変数を作成：　`names := []string{"A", "B", "C"}`
- マップ
    - `map[KeyType]ValueType`
    - 初期化：　make 関数を使う
        - `make(map[string]int)`
    - マップでキーと値を関連づける
        - `messages[name] = message`
- ルーン
    - `type rune = int32`
    - rune は int32 のエイリアスであり、あらゆる点で int32 と同等
    - 慣例により、文字値と整数値を区別するために使用される

# テスト系

- `AAA_test.go`
    - ファイル末尾に `_test.go` がある場合、 `go test` コマンドはそのファイルにテスト関数が含まれると判断する
- `func TestName(t *testing.T) { ... }`
    - テスト関数の頭には `Test` をつける
    - `testing` パッケージの `testing.T` 型へのポインタをパラメータとして受け取る
    - このパラメータのメソッドを使用して、テストからのレポートとログを記録する
- `go test`
    - テストを実行する
        
        ```bash
        $ go test
        PASS
        ok      example.com/greetings   0.591s
        ```
        
    - すべてのテストとその結果をリストする詳細な出力を取得する
        
        ```bash
        $ go test -v
        === RUN   TestHelloName
        --- PASS: TestHelloName (0.00s)
        === RUN   TestHelloEmpty
        --- PASS: TestHelloEmpty (0.00s)
        PASS
        ok      example.com/greetings   0.125s
        ```
        

