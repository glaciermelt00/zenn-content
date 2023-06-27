---
title: "Return greetings for multiple people"
---

- `greetings/greetings.go` で、コードを変更
  
  ```go
  // Hellos returns a map that associates each of the named people
  // with a greeting message.
  func Hellos(names []string) (map[string]string, error) {
    // A map to associate names with messages.
    messages := make(map[string]string)
    // Loop through the received slice of names, calling
    // the Hello function to get a message for each name.
    for _, name := range names {
      message, err := Hello(name)
      if err != nil {
          return nil, err
      }
      // In the map, associate the retrieved message with
      // the name.
      messages[name] = message
    }
    return messages, nil
  }
  ```
  
  - `Hellos` 関数を追加：　パラメータは名前のスライス：　単一の名前ではない
    - 戻り値の型を変更：　`string` から `map` へ：　挨拶メッセージにマッピングされた名前を返せる
  - 新規の `Hellos` 関数が既存の `Hello` を呼び出す
    - 重複を減らすのに役立つ：　2つの関数も維持する一方で
  - `messages` マップを作る：　（キーとして）受信した名前それぞれに（値として）生成されたメッセージを関連づけるため
    - Go では、次の構文で `map` を初期化する：　`map` [ *key-type* ] *value-type*
    - `Hellos` 関数はこの `map` を呼び出し側に返す
  - 関数が受け取った名前をループする：　それぞれの値が空でないことを確認しながら：　それぞれにメッセージを関連づける
    - インデックスは不要：　Go のブランク識別子（アンダースコア）を使用して無視する
- コードを呼び出す `hello/hello.go` で、名前のスライスを渡す：　返された名前/メッセージのマップの内容を出力する
  ```go
  package main

  import (
      "fmt"
      "log"

      "example.com/greetings"
  )

  func main() {
      // Set properties of the predefined Logger, including
      // the log entry prefix and a flag to disable printing
      // the time, source file, and line number.
      log.SetPrefix("greetings: ")
      log.SetFlags(0)

      // A slice of names.
      names := []string{"Gladys", "Samantha", "Darrin"}

      // Request greeting messages for the names.
      messages, err := greetings.Hellos(names)
      if err != nil {
          log.Fatal(err)
      }
      // If no error was returned, print the returned map of
      // messages to the console.
      fmt.Println(messages)
  }
  ```
  - `names` 変数を作成：　3つの名前を保持するスライス型として
  - `names` 変数を渡す：　`Hellos` 関数に引数として
- コマンドラインで、 `hello/hello.go` を含むディレクトリへ変更：　`go run` を使う：　コードが機能することを確認するため
  ```bash
  $ go run.
  map[Darrin:Hail, Darrin! Well met! Gladys:Hi, Gladys. Welcome! Samantha:Great to see you, Samantha!]
  ```
