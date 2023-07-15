---
title: "メモ"
---

# コマンド系

- バージョン確認
    
    ```bash
    $ go version
    ```
    
- コードの実行
    
    ```bash
    $ go run .
    ```
    
    - モジュールを指定して実行：　example/hello モジュールを指定
        
        ```bash
        $ go run example/hello
        ```
        
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
- 変数宣言
    - `var i int`
        - `int` 型の変数 `i` を宣言
    - `var i, j int = 1, 2`
        - `int` 型の変数 `i` と `j` を宣言し、初期化
    - `k := 3`
        - `int` 型の変数 `k` を宣言し、初期化
        - `:=` は、変数の宣言と初期化を同時に行う
        - 関数の中でのみ使用できる
    - `var i int`
        - 変数に初期値を与えずに宣言すると、ゼロ値が与えられる
        - 数値型: 0
        - bool 型: false
        - string 型: ""
    - `var f float64 = float64(i)`
        - 型変換: 変数 v, 型 T がある場合、T(v) は変数 v をT 型へ変換する
        - シンプルに書ける
            - `f := float64(i)`
    - `i := 42 // int`
        - 型推論: 明示的な値を指定せずに変数を宣言する場合、変数の型は右側の変数か、型推論される
    - `const World = "世界"`
        - 定数: const キーワードを使って、変数と同じように宣言できる
        - 変数は、文字、文字列、boolean、数値のみで使える
        - 数値の定数: 高精度な値
            - 型のない定数は、その状況によって必要な型をとる
- `for`
    ```go
    for i := 0; i < 10; i++ {
        sum += i
    }
    ```
        - 初期ステートメント、条件式、後処理ステートメントで構成される
        - 中括弧は常に必要

    ```go
    sum := 1
    for ; sum < 1000; {
        sum += sum
    }
    ```
        - 初期化と後処理ステートメントの技術は任意

    ```go
    sum := 1
    for sum < 1000 {
        sum += sum
    }
    ```
        - セミコロンを省略できる
        - 他言語での while のような使い方

    ```go
    for {
    }
    ```
        - ループ条件式を省略すれば、無限ループになる
- `if`
    ```go
    if x < 0 {
        return sqrt(-x) + "i"
    }
    ```
        - 括弧は不要で、中括弧は必要

    ```go
    if v := math.Pow(x, n); v < lim {
        return v
    }
    ```
        - 条件の前に、評価す？ための簡単なステートメントを書ける
        - ここで宣言された変数は、 if のスコープ内だけで有効

    ```go
    if v := math.Pow(x, n); v < lim {
        return v
    } else {
        fmt.Printf("%g >= %g\n", v, lim)
    }
    ```
        - if ステートメントで宣言された変数は、 else ブロック内でも使える

# パッケージ系

- `fmt` パッケージ
    - https://pkg.go.dev/fmt
    - `Println` 関数：　オペランドのデフォルト形式を使用してフォーマットし、標準出力に書き込む
        - オペランドの間には常にスペースが追加され、改行が追加される
        - 書き込まれたバイト数と、発生した書き込みエラーを返す
    - `Sprintf` 関数：　フォーマット指定子に従ってフォーマットし、結果を返す
    - `Errorf` 関数：　フォーマット指定子に従ってフォーマットを設定し、文字列を error を満たす値として返す
    - `Printf` 関数：　フォーマット指定子に従ってフォーマットし、標準出力に書き込む
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
    - `Println` 関数：　Output を呼び出して、標準ロガーに出力する
- `math/rand` パッケージ
    - https://pkg.go.dev/math/rand
    - `Intn` 関数：　`int` として、非負の擬似ランダムな数を返す：　デフォルトの Source から半開区間 `[0, n)` で
        - n が 0以下の場合、パニックになる
- `testing` パッケージ
    - `T` 型：　テスト状態を管理し、フォーマットされたテストログをサポートするために、テスト関数に渡される型
        - `Fatalf` 関数：　`Logf` の後に `FailNow` が続くものと同等
    - `F` 型：　fuzz テストに渡される型
        - `Add` 関数：　fuzz テストのシードコーパスに引数を追加する
        - `Fuzz` 関数：　fuzz テストのために fuzz 関数 ff を実行する
            - 一覧の引数に対して ff が失敗した場合、それらの引数はシードコーパスに追加される。
- `regexp` パッケージ
    - `MustCompile(str string) *Regexp` 関数：　Compile に似ているが、式を解析できない場合にパニックを起こす
        - これにより、コンパイルされた正規表現を保持するグローバル変数の安全な初期化が簡素化される
    - `MatchString` 関数：　文字列 s に正規表現パターンの一致が含まれているかどうかを報告する
- `unicode` パッケージ
    - https://pkg.go.dev/unicode
    - `ToUpper` 関数：　rune を大文字にマップする
- `database/sql` パッケージ
    - https://pkg.go.dev/database/sql
    - データベースへの接続、トランザクションの実行、進行中の操作のキャンセルなどのための型と関数が含まれる
    - `ErrNoRows` 変数：　QueryROw が行を返さない場合に Scan によって返される
    - `DB` 型：　0 個以上の基礎となる接続のプールを表すデータベースハンドル
        - `Open` 関数：　データベースドライバ名とドライバー固有のデータソース名で指定されたデータベースを開く
        - `Ping` 関数：　データベースへの接続がまだ有効であることを確認し、必要に応じて接続を確立する
        - `Query` 関数：　行を返すクエリ（通常は　SELECT）を実行する
            - 引数は、クエリ内のプレースホルダーパラメータ用
        - `QueryRow` 関数：　最大 1 行を返すことが期待されるクエリを実行する
            - 常に非 nil 値を返す
            - エラーは、 Row の Scan メソッドが呼び出されるまで延期される
            - クエリで行が選択されていない場合、 *Row のスキャンは ErrNoRows を返す
        - `Exec` 関数：　行を返さずにクエリを実行する
            - 引数は、クエリ内のプレースホルダーパラメータ用
    - `Rows` 型：　クエリの結果
        - そのカーソルは、結果セットの最初の行の前から始まる
        - Next 関数を使用して行から行に進む
        - `Close` 関数：　Rows を閉じ、それ以上の列挙を防ぐ
        - `Next` 関数：　Scan 関数で読み取るために次の結果行を準備する
        - `Scan` 関数：　現在の行の列を dest が指す位置にコピーする
        - `Err` 関数：　反復中に発生したエラーがあれば返す
    - `Row` 型：　QueryRow を呼び出して単一の行を選択した結果
        - `Scan` 関数：　一致した行の列を dest が指す値にコピーする
            - 複数の行が一致する場合、 Scan は最初の行を使用し、残りの行を破棄する
            - クエリに一致する行がない場合、 Scan は ErrNoRows を返す
    - `Result` 型：　実行された SQL コマンドが要約される
        - `LastInsertId` 関数：　コマンドに応答してデータベースが生成された整数
- `mysql` パッケージ
    - https://pkg.go.dev/github.com/go-sql-driver/mysql
    - `Config` 型：　DSN 文字列から解析された構成
        - DSN 文字列から解析するのではなく、新しい `Config` を作成する場合は、デフォルト値を設定する `NewConfig` 関数を使用する必要がある
        - `FormatDSN` 関数：　指定された `Config` をドライバに渡すことができる DSN 文字列にフォーマットする
- `builtin` パッケージ
    - https://pkg.go.dev/builtin
    - `append` 関数： 要素をスライスの末尾に追加する
- `gin-gonic/gin` パッケージ
    - https://pkg.go.dev/github.com/gin-gonic/gin
    - `Context` 型：　Gin の最も重要な部分
        - これにより、ミドルウェア間で変数を渡したり、フローを管理したり、リクエストの JSON を検証したり、 JSON レスポンスをレンダリングしたりできる
        - `IndentedJSON` 関数：　指定された構造体を適切な JSON (インデント + エンドライン) としてレスポンスボディにシリアル化する
        - `JSON` 関数：　指定された構造体を JSON としてレスポンスボディにシリアル化する
            - Content-Type を `application-json` に設定する
        - `BindJSON` 関数：　c.MustBindWith(obj, binding.JSON) のショートカット
        - `MustBindWith` 関数：　指定されたビンディングエンジンを使用して、渡された構造体ポインターをバインドする
        - `Param` 関数：　URL パラメータの値を返す
            - c.Params.ByName(key) のショートカット
        - `Bind` 関数：　Method と Content-Type をチェックしてバインディングエンジンを自動的に選択する
            - Content-TYpe == "application/json" の場合、 JSON または XML を JSON 入力として使用して、リクエストの本文を JSON として解析する
        - `ShouldBind` 関数：　Method と Content-Type をチェックしてバインディングエンジンを自動的に選択する
            - c.Bind() と似ているが、このメソッドは応答ステータスコードを 400 に設定したり、入力が有効でない場合に中止したりしない
        - `ShouldBindUri` 関数：　指定されたバインディングエンジンを使用して、渡された構造体ポインターをバインドする
    - `Params` 型：　キーと値で構成される単一の URL パラメータ
        - `ByName` 関数：　キーが指定された名前に一致する最初の Param の値を返す
            - 一致する Param が見つからない場合は、空の文字列が返される
    - `Engine` 型：　フレームワークのインスタンスであり、マルチプレクサー、ミドルウェア、構成設定が含まれる
        - `Default` 関数：　Logger および Recovery ミドルウェアが既にアタッチされている Engine インスタンスが返される
        - `Run` 関数：　ルーターを http.Server に接続し、 HTTP リクエストのリッスンと処理を開始する
            - http.ListenAndServe 関数のショートカット
    - `RouterGroup` 型：　ルーターを構成するために内部的に使用され、プレフィックスとハンドラー（ミドルウェア）の配列に関連づけられる
        - `GET` 関数：　router.Handle("GET", path, handlers) のショートカット
        - `Handle` 関数：　指定されたパスとメソッドを使用して、新しいリクエストハンドルとミドルウェアを登録する
        - `POST` 関数：　router.Handle("POST", path, handlers) のショートカット
    - `H` 型：　map[string]any のショートカット
    - `DisableConsoleColor` 関数：　コンソールでのカラー出力を無効にする
    - `ForceConsoleColor` 関数：　コンソールでのカラー出力を強制する
- `http` パッケージ
    - https://pkg.go.dev/net/http
    - `StatusOK` 定数：　HTTP ステータスコード 200
    - `StatusCreated` 定数：　HTTP ステータスコード 201
    - `StatusNotFound` 定数：　HTTP ステータスコード 404
- `binding` パッケージ
    - https://pkg.go.dev/github.com/gin-gonic/gin/binding
    - `JSON` 変数：　jsonBinding{}
        - Binding インターフェイスを実装しており、リクエストに含まれるデータを構造体インスタンスにバインドするために使用できる
    - `Uri` 変数：　uriBinding{}
    - `Binding` 型：　JSON リクエスト本文、クエリパラメータ、フォーム POST などのリクエスト内に存在するデータをバインドするために実装する必要があるインターフェイスを記述する
- `unicode/utf8` パッケージ
    - https://pkg.go.dev/unicode/utf8
    - `ValidString` 関数：　完全に有効な UTF-8 でエンコードされたルーンで構成されているかどうかを報告する
    - `RuneCountInString` 関数：　RuenCount に似ているが、その入力は文字列
- `time` パッケージ
    - https://pkg.go.dev/time
    - `Time` 型：　ナノ秒の精度で瞬間を表す

# モジュール系

- `go mod init` で依存性追跡を有効にする
    
    ```bash
    $ go mod init <prefix>/<descriptive-text>
    ```
    
    - prefix: モジュールを部分的に説明する文字列
    - descriptive-text: プロジェクト名
        - https://go.dev/doc/modules/managing-dependencies#naming_module
- `go mod tidy` で新規モジュールの要件・サムを追加する
    
    ```bash
    $ go mod tidy
    ```
    
- ローカルのモジュールを適用する
    - `go mod edit -replace` を使う
        
        ```bash
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
- `go get` で依存関係を追加する
    
    ```bash
    $ go get golang.org/x/example
    go: downloading golang.org/x/example v0.0.0-20230515183114-5bec75697667
    go: added golang.org/x/example v0.0.0-20230515183114-5bec75697667
    ```
    - `golang.org/x/example` モジュールに依存関係を追加

# 型

- 組み込み型
    - bool
    - string
    - 整数: int, int8, int16, int64, uint, uint8, uint16, uint32, uint64, uintptr
    - byte: utint8 の別名
    - rune: int32 の別名: Unicode のコードポイントを表す
    - 浮動小数点数: float32, float64
    - 複素数: complex64, complex128
        - factored に宣言できる
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

# 構文系
- `defer`
    - 関数が return するまで、関数の実行を延期する
        
        ```go
        defer rows.Close()
        ```
        

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
        
- `go test -fuzz=Fuzz`
    - fuzz テストを実行する
- `go test -run=FuzzReverse/82c78cde10256ca2`
    - 特定のコーパスエントリを実行する
- `go test -fuzz=Fuzz -fuzztime 30s`
    - 30 秒間 fuzz テストを実行し、障害が見つからなかった場合に終了する

# JSON 系

- struct の定義
    - `json:"..."` のように、フィールドタグを付ける
    
    ```go
    type album struct {
        ID     string  `json:"id"`
        Title  string  `json:"title"`
        Artist string  `json:"artist"`
        Price  float64 `json:"price"`
    }
    ```
    

# ジェネリクス

- `comparable` 型
    - https://go.dev/blog/comparable#comparable-types
    - `==` と `!=` で比較できる型
