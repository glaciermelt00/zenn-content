---
title: "Gin のクイックスタート"
---

```bash
$ mkdir example-gin
$ cd example-gin

// go get でエラーが出る
$ go get -u github.com/gin-gonic/gin
go: go.mod file not found in current directory or any parent directory.
        'go get' is no longer supported outside a module.
        To build and install a command, use 'go install' with a version,
        like 'go install example.com/cmd@latest'
        For more information, see https://golang.org/doc/go-get-install-deprecation
        or run 'go help get' or 'go help install'.
$ ls -a
.  ..

// モジュールを初期化する
$ go mod init glaciermelt00/example-gin
go: creating new go.mod: module glaciermelt00/example-gin
$ ls -a
.  ..  go.mod
$ cat go.mod
module glaciermelt00/example-gin

go 1.20

// もう一度 go get する
$ go get -u github.com/gin-gonic/gin
go: downloading golang.org/x/net v0.11.0
go: downloading google.golang.org/protobuf v1.31.0
go: downloading github.com/go-playground/validator/v10 v10.14.1
go: downloading github.com/ugorji/go v1.2.11
go: downloading golang.org/x/sys v0.10.0
go: downloading github.com/pelletier/go-toml v1.9.5
go: downloading github.com/go-playground/validator v9.31.0+incompatible
go: downloading github.com/bytedance/sonic v1.9.2
go: downloading golang.org/x/text v0.11.0
go: downloading golang.org/x/crypto v0.10.0
go: downloading golang.org/x/arch v0.4.0
go: downloading github.com/klauspost/cpuid v1.3.1
go: downloading github.com/klauspost/cpuid/v2 v2.2.5
go: added github.com/bytedance/sonic v1.9.2
go: added github.com/chenzhuoyu/base64x v0.0.0-20221115062448-fe3a3abad311
go: added github.com/gabriel-vasile/mimetype v1.4.2
go: added github.com/gin-contrib/sse v0.1.0
go: added github.com/gin-gonic/gin v1.9.1
go: added github.com/go-playground/locales v0.14.1
go: added github.com/go-playground/universal-translator v0.18.1
go: added github.com/go-playground/validator/v10 v10.14.1
go: added github.com/goccy/go-json v0.10.2
go: added github.com/json-iterator/go v1.1.12
go: added github.com/klauspost/cpuid/v2 v2.2.5
go: added github.com/leodido/go-urn v1.2.4
go: added github.com/mattn/go-isatty v0.0.19
go: added github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd
go: added github.com/modern-go/reflect2 v1.0.2
go: added github.com/pelletier/go-toml/v2 v2.0.8
go: added github.com/twitchyliquid64/golang-asm v0.15.1
go: added github.com/ugorji/go/codec v1.2.11
go: added golang.org/x/arch v0.4.0
go: added golang.org/x/crypto v0.10.0
go: added golang.org/x/net v0.11.0
go: added golang.org/x/sys v0.10.0
go: added golang.org/x/text v0.11.0
go: added google.golang.org/protobuf v1.31.0
go: added gopkg.in/yaml.v3 v3.0.1
$ ls -a
.  ..  go.mod  go.sum

// go.mod の中身を確認
$ cat go.mod
module glaciermelt00/example-gin

go 1.20

require (
        github.com/bytedance/sonic v1.9.2 // indirect
        github.com/chenzhuoyu/base64x v0.0.0-20221115062448-fe3a3abad311 // indirect
        github.com/gabriel-vasile/mimetype v1.4.2 // indirect
        github.com/gin-contrib/sse v0.1.0 // indirect
        github.com/gin-gonic/gin v1.9.1 // indirect
        github.com/go-playground/locales v0.14.1 // indirect
        github.com/go-playground/universal-translator v0.18.1 // indirect
        github.com/go-playground/validator/v10 v10.14.1 // indirect
        github.com/goccy/go-json v0.10.2 // indirect
        github.com/json-iterator/go v1.1.12 // indirect
        github.com/klauspost/cpuid/v2 v2.2.5 // indirect
        github.com/leodido/go-urn v1.2.4 // indirect
        github.com/mattn/go-isatty v0.0.19 // indirect
        github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd // indirect
        github.com/modern-go/reflect2 v1.0.2 // indirect
        github.com/pelletier/go-toml/v2 v2.0.8 // indirect
        github.com/twitchyliquid64/golang-asm v0.15.1 // indirect
        github.com/ugorji/go/codec v1.2.11 // indirect
        golang.org/x/arch v0.4.0 // indirect
        golang.org/x/crypto v0.10.0 // indirect
        golang.org/x/net v0.11.0 // indirect
        golang.org/x/sys v0.10.0 // indirect
        golang.org/x/text v0.11.0 // indirect
        google.golang.org/protobuf v1.31.0 // indirect
        gopkg.in/yaml.v3 v3.0.1 // indirect
)

// go.sum の中身を確認
$ cat go.sum
github.com/bytedance/sonic v1.5.0/go.mod h1:ED5hyg4y6t3/9Ku1R6dU/4KyJ48DZ4jPhfY1O2AihPM=
github.com/bytedance/sonic v1.9.2 h1:GDaNjuWSGu09guE9Oql0MSTNhNCLlWwO8y/xM5BzcbM=
github.com/bytedance/sonic v1.9.2/go.mod h1:i736AoUSYt75HyZLoJW9ERYxcy6eaN6h4BZXU064P/U=
github.com/chenzhuoyu/base64x v0.0.0-20211019084208-fb5309c8db06/go.mod h1:DH46F32mSOjUmXrMHnKwZdA8wcEefY7UVqBKYGjpdQY=
github.com/chenzhuoyu/base64x v0.0.0-20221115062448-fe3a3abad311 h1:qSGYFH7+jGhDF8vLC+iwCD4WpbV1EBDSzWkJODFLams=
github.com/chenzhuoyu/base64x v0.0.0-20221115062448-fe3a3abad311/go.mod h1:b583jCggY9gE99b6G5LEC39OIiVsWj+R97kbl5odCEk=
github.com/davecgh/go-spew v1.1.0/go.mod h1:J7Y8YcW2NihsgmVo/mv3lAwl/skON4iLHjSsI+c5H38=
github.com/davecgh/go-spew v1.1.1/go.mod h1:J7Y8YcW2NihsgmVo/mv3lAwl/skON4iLHjSsI+c5H38=
github.com/gabriel-vasile/mimetype v1.4.2 h1:w5qFW6JKBz9Y393Y4q372O9A7cUSequkh1Q7OhCmWKU=
github.com/gabriel-vasile/mimetype v1.4.2/go.mod h1:zApsH/mKG4w07erKIaJPFiX0Tsq9BFQgN3qGY5GnNgA=
github.com/gin-contrib/sse v0.1.0 h1:Y/yl/+YNO8GZSjAhjMsSuLt29uWRFHdHYUb5lYOV9qE=
github.com/gin-contrib/sse v0.1.0/go.mod h1:RHrZQHXnP2xjPF+u1gW/2HnVO7nvIa9PG3Gm+fLHvGI=
github.com/gin-gonic/gin v1.9.1 h1:4idEAncQnU5cB7BeOkPtxjfCSye0AAm1R0RVIqJ+Jmg=
github.com/gin-gonic/gin v1.9.1/go.mod h1:hPrL7YrpYKXt5YId3A/Tnip5kqbEAP+KLuI3SUcPTeU=
github.com/go-playground/locales v0.14.1 h1:EWaQ/wswjilfKLTECiXz7Rh+3BjFhfDFKv/oXslEjJA=
github.com/go-playground/locales v0.14.1/go.mod h1:hxrqLVvrK65+Rwrd5Fc6F2O76J/NuW9t0sjnWqG1slY=
github.com/go-playground/universal-translator v0.18.1 h1:Bcnm0ZwsGyWbCzImXv+pAJnYK9S473LQFuzCbDbfSFY=
github.com/go-playground/universal-translator v0.18.1/go.mod h1:xekY+UJKNuX9WP91TpwSH2VMlDf28Uj24BCp08ZFTUY=
github.com/go-playground/validator/v10 v10.14.1 h1:9c50NUPC30zyuKprjL3vNZ0m5oG+jU0zvx4AqHGnv4k=
github.com/go-playground/validator/v10 v10.14.1/go.mod h1:9iXMNT7sEkjXb0I+enO7QXmzG6QCsPWY4zveKFVRSyU=
github.com/goccy/go-json v0.10.2 h1:CrxCmQqYDkv1z7lO7Wbh2HN93uovUHgrECaO5ZrCXAU=
github.com/goccy/go-json v0.10.2/go.mod h1:6MelG93GURQebXPDq3khkgXZkazVtN9CRI+MGFi0w8I=
github.com/golang/protobuf v1.5.0/go.mod h1:FsONVRAS9T7sI+LIUmWTfcYkHO4aIWwzhcaSAoJOfIk=
github.com/google/go-cmp v0.5.5/go.mod h1:v8dTdLbMG2kIc/vJvl+f65V22dbkXbowE6jgT/gNBxE=
github.com/google/gofuzz v1.0.0/go.mod h1:dBl0BpW6vV/+mYPU4Po3pmUjxk6FQPldtuIdl/M65Eg=
github.com/json-iterator/go v1.1.12 h1:PV8peI4a0ysnczrg+LtxykD8LfKY9ML6u2jnxaEnrnM=
github.com/json-iterator/go v1.1.12/go.mod h1:e30LSqwooZae/UwlEbR2852Gd8hjQvJoHmT4TnhNGBo=
github.com/klauspost/cpuid/v2 v2.0.9/go.mod h1:FInQzS24/EEf25PyTYn52gqo7WaD8xa0213Md/qVLRg=
github.com/klauspost/cpuid/v2 v2.2.5 h1:0E5MSMDEoAulmXNFquVs//DdoomxaoTY1kUhbc/qbZg=
github.com/klauspost/cpuid/v2 v2.2.5/go.mod h1:Lcz8mBdAVJIBVzewtcLocK12l3Y+JytZYpaMropDUws=
github.com/leodido/go-urn v1.2.4 h1:XlAE/cm/ms7TE/VMVoduSpNBoyc2dOxHs5MZSwAN63Q=
github.com/leodido/go-urn v1.2.4/go.mod h1:7ZrI8mTSeBSHl/UaRyKQW1qZeMgak41ANeCNaVckg+4=
github.com/mattn/go-isatty v0.0.19 h1:JITubQf0MOLdlGRuRq+jtsDlekdYPia9ZFsB8h/APPA=
github.com/mattn/go-isatty v0.0.19/go.mod h1:W+V8PltTTMOvKvAeJH7IuucS94S2C6jfK/D7dTCTo3Y=
github.com/modern-go/concurrent v0.0.0-20180228061459-e0a39a4cb421/go.mod h1:6dJC0mAP4ikYIbvyc7fijjWJddQyLn8Ig3JB5CqoB9Q=
github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd h1:TRLaZ9cD/w8PVh93nsPXa1VrQ6jlwL5oN8l14QlcNfg=
github.com/modern-go/concurrent v0.0.0-20180306012644-bacd9c7ef1dd/go.mod h1:6dJC0mAP4ikYIbvyc7fijjWJddQyLn8Ig3JB5CqoB9Q=
github.com/modern-go/reflect2 v1.0.2 h1:xBagoLtFs94CBntxluKeaWgTMpvLxC4ur3nMaC9Gz0M=
github.com/modern-go/reflect2 v1.0.2/go.mod h1:yWuevngMOJpCy52FWWMvUC8ws7m/LJsjYzDa0/r8luk=
github.com/pelletier/go-toml/v2 v2.0.8 h1:0ctb6s9mE31h0/lhu+J6OPmVeDxJn+kYnJc2jZR9tGQ=
github.com/pelletier/go-toml/v2 v2.0.8/go.mod h1:vuYfssBdrU2XDZ9bYydBu6t+6a6PYNcZljzZR9VXg+4=
github.com/pmezard/go-difflib v1.0.0/go.mod h1:iKH77koFhYxTK1pcRnkKkqfTogsbg7gZNVY4sRDYZ/4=
github.com/stretchr/objx v0.1.0/go.mod h1:HFkY916IF+rwdDfMAkV7OtwuqBVzrE8GR6GFx+wExME=
github.com/stretchr/objx v0.4.0/go.mod h1:YvHI0jy2hoMjB+UWwv71VJQ9isScKT/TqJzVSSt89Yw=
github.com/stretchr/objx v0.5.0/go.mod h1:Yh+to48EsGEfYuaHDzXPcE3xhTkx73EhmCGUpEOglKo=
github.com/stretchr/testify v1.3.0/go.mod h1:M5WIy9Dh21IEIfnGCwXGc5bZfKNJtfHm1UVUgZn+9EI=
github.com/stretchr/testify v1.7.0/go.mod h1:6Fq8oRcR53rry900zMqJjRRixrwX3KX962/h/Wwjteg=
github.com/stretchr/testify v1.7.1/go.mod h1:6Fq8oRcR53rry900zMqJjRRixrwX3KX962/h/Wwjteg=
github.com/stretchr/testify v1.8.0/go.mod h1:yNjHg4UonilssWZ8iaSj1OCr/vHnekPRkoO+kdMU+MU=
github.com/stretchr/testify v1.8.1/go.mod h1:w2LPCIKwWwSfY2zedu0+kehJoqGctiVI29o6fzry7u4=
github.com/stretchr/testify v1.8.2/go.mod h1:w2LPCIKwWwSfY2zedu0+kehJoqGctiVI29o6fzry7u4=
github.com/stretchr/testify v1.8.3/go.mod h1:sz/lmYIOXD/1dqDmKjjqLyZ2RngseejIcXlSw2iwfAo=
github.com/twitchyliquid64/golang-asm v0.15.1 h1:SU5vSMR7hnwNxj24w34ZyCi/FmDZTkS4MhqMhdFk5YI=
github.com/twitchyliquid64/golang-asm v0.15.1/go.mod h1:a1lVb/DtPvCB8fslRZhAngC2+aY1QWCk3Cedj/Gdt08=
github.com/ugorji/go/codec v1.2.11 h1:BMaWp1Bb6fHwEtbplGBGJ498wD+LKlNSl25MjdZY4dU=
github.com/ugorji/go/codec v1.2.11/go.mod h1:UNopzCgEMSXjBc6AOMqYvWC1ktqTAfzJZUZgYf6w6lg=
golang.org/x/arch v0.0.0-20210923205945-b76863e36670/go.mod h1:5om86z9Hs0C8fWVUuoMHwpExlXzs5Tkyp9hOrfG7pp8=
golang.org/x/arch v0.4.0 h1:A8WCeEWhLwPBKNbFi5Wv5UTCBx5zzubnXDlMOFAzFMc=
golang.org/x/arch v0.4.0/go.mod h1:5om86z9Hs0C8fWVUuoMHwpExlXzs5Tkyp9hOrfG7pp8=
golang.org/x/crypto v0.10.0 h1:LKqV2xt9+kDzSTfOhx4FrkEBcMrAgHSYgzywV9zcGmM=
golang.org/x/crypto v0.10.0/go.mod h1:o4eNf7Ede1fv+hwOwZsTHl9EsPFO6q6ZvYR8vYfY45I=
golang.org/x/net v0.11.0 h1:Gi2tvZIJyBtO9SDr1q9h5hEQCp/4L2RQ+ar0qjx2oNU=
golang.org/x/net v0.11.0/go.mod h1:2L/ixqYpgIVXmeoSA/4Lu7BzTG4KIyPIryS4IsOd1oQ=
golang.org/x/sys v0.5.0/go.mod h1:oPkhp1MJrh7nUepCBck5+mAzfO9JrbApNNgaTdGDITg=
golang.org/x/sys v0.6.0/go.mod h1:oPkhp1MJrh7nUepCBck5+mAzfO9JrbApNNgaTdGDITg=
golang.org/x/sys v0.10.0 h1:SqMFp9UcQJZa+pmYuAKjd9xq1f0j5rLcDIk0mj4qAsA=
golang.org/x/sys v0.10.0/go.mod h1:oPkhp1MJrh7nUepCBck5+mAzfO9JrbApNNgaTdGDITg=
golang.org/x/text v0.11.0 h1:LAntKIrcmeSKERyiOh0XMV39LXS8IE9UL2yP7+f5ij4=
golang.org/x/text v0.11.0/go.mod h1:TvPlkZtksWOMsz7fbANvkp4WM8x/WCo/om8BMLbz+aE=
golang.org/x/xerrors v0.0.0-20191204190536-9bdfabe68543/go.mod h1:I/5z698sn9Ka8TeJc9MKroUUfqBBauWjQqLJ2OPfmY0=
google.golang.org/protobuf v1.26.0-rc.1/go.mod h1:jlhhOSvTdKEhbULTjvd4ARK9grFBp09yW+WbY/TyQbw=
google.golang.org/protobuf v1.31.0 h1:g0LDEJHgrBl9N9r17Ru3sqWhkIx2NB67okBHPwC7hs8=
google.golang.org/protobuf v1.31.0/go.mod h1:HV8QOd/L58Z+nl8r43ehVNZIU/HEI6OcFqwMG9pJV4I=
gopkg.in/check.v1 v0.0.0-20161208181325-20d25e280405/go.mod h1:Co6ibVJAznAaIkqp8huTwlJQCZ016jof/cbN4VW5Yz0=
gopkg.in/yaml.v3 v3.0.0-20200313102051-9f266ea9e77c/go.mod h1:K4uyk7z7BCEPqu6E+C64Yfv1cQ7kz7rIZviUmN+EgEM=
gopkg.in/yaml.v3 v3.0.1 h1:fxVm/GzAzEWqLHuvctI91KS9hhNmmWOoWu0XTYJS7CA=
gopkg.in/yaml.v3 v3.0.1/go.mod h1:K4uyk7z7BCEPqu6E+C64Yfv1cQ7kz7rIZviUmN+EgEM=
rsc.io/pdf v0.1.1/go.mod h1:n8OzWcQ6Sp37PL01nO98y4iUCRdTGarVfzxY20ICaU4=

// main.go ファイルを作成
$ touch main.go

// main.go で gin と http をインポート
```

VSCode でエラーが出ていたため、ドキュメントを元に少し修正


```bash
// $GOPATH/src 配下にディレクトリを作成し、移動する
$ mkdir -p $HOME/go/src/github.com/glaciermelt00/example-gin && cd "$_"
$ pwd
/Users/glaciermelt/go/src/github.com/glaciermelt00/example-gin
$ ls

// テンプレートをコピーする
$ curl https://raw.githubusercontent.com/gin-gonic/examples/master/basic/main.go > main.go

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1588  100  1588    0     0   3370      0 --:--:-- --:--:-- --:--:--  3393
$ ls -a
.  ..  main.go

// go run したが、 go.mod ファイルがないと言われる
$ go run main.go
main.go:6:2: no required module provides package github.com/gin-gonic/gin: go.mod file not found in current directory or any parent directory; see 'go help modules'
$ ls
main.go

// go get したが、 go.mod ファイルがないと言われる
$ go get -u github.com/gin-gonic/gin
go: go.mod file not found in current directory or any parent directory.
        'go get' is no longer supported outside a module.
        To build and install a command, use 'go install' with a version,
        like 'go install example.com/cmd@latest'
        For more information, see https://golang.org/doc/go-get-install-deprecation
        or run 'go help get' or 'go help install'.

// go init する
$ go mod init github.com/glaciermelt00/example-gin
go: creating new go.mod: module github.com/glaciermelt00/example-gin
go: to add module requirements and sums:
        go mod tidy

// go mod tidy する
$ go mod tidy
go: finding module for package github.com/gin-gonic/gin
go: found github.com/gin-gonic/gin in github.com/gin-gonic/gin v1.9.1

// go run する
// 以下の警告ウィンドウが出た
//// アプリケーション“main”へのネットワーク受信接続を許可しますか?
//// “拒否”をクリックすると、アプリケーションの一部の機能が利用できなくなることがあります。この設定は“セキュリティとプライバシー”環境設定の“ファイアウォール”パネルで変更できます。
// 許可しておく
$ go run main.go
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /ping                     --> main.setupRouter.func1 (3 handlers)
[GIN-debug] GET    /user/:name               --> main.setupRouter.func2 (3 handlers)
[GIN-debug] POST   /admin                    --> main.setupRouter.func3 (4 handlers)
[GIN-debug] [WARNING] You trusted all proxies, this is NOT safe. We recommend you to set a value.
Please check https://pkg.go.dev/github.com/gin-gonic/gin#readme-don-t-trust-all-proxies for details.
[GIN-debug] Listening and serving HTTP on :8080
```

- AsciiJSON
    - AsciiJSON を使って、エスケープされた非 ASCII 文字列から ASCII のみの JSON を生成する
        ``` go
        func main() {
          r := gin.Default()

          r.GET("/someJSON", func(c *gin.Context) {
            data := map[string]interface{}{
              "lang": "GO语言",
              "tag":  "<br>",
            }

            // will output : {"lang":"GO\u8bed\u8a00","tag":"\u003cbr\u003e"}
            c.AsciiJSON(http.StatusOK, data)
          })

          // Listen and serve on 0.0.0.0:8080
          r.Run(":8080")
        }
        ```
- フォームデータリクエストを、カスタム struct にバインドする
    - カスタム struct にバインドできる
        ```go
        type StructA struct {
            FieldA string `form:"field_a"`
        }

        type StructB struct {
            NestedStruct StructA
            FieldB string `form:"field_b"`
        }

        type StructC struct {
            NestedStructPointer *StructA
            FieldC string `form:"field_c"`
        }

        type StructD struct {
            NestedAnonyStruct struct {
                FieldX string `form:"field_x"`
            }
            FieldD string `form:"field_d"`
        }

        func GetDataB(c *gin.Context) {
            var b StructB
            c.Bind(&b)
            c.JSON(200, gin.H{
                "a": b.NestedStruct,
                "b": b.FieldB,
            })
        }

        func GetDataC(c *gin.Context) {
            var b StructC
            c.Bind(&b)
            c.JSON(200, gin.H{
                "a": b.NestedStructPointer,
                "c": b.FieldC,
            })
        }

        func GetDataD(c *gin.Context) {
            var b StructD
            c.Bind(&b)
            c.JSON(200, gin.H{
                "x": b.NestedAnonyStruct,
                "d": b.FieldD,
            })
        }

        func main() {
            r := gin.Default()
            r.GET("/getb", GetDataB)
            r.GET("/getc", GetDataC)
            r.GET("/getd", GetDataD)

            r.Run()
        }
        ```
    - curl の結果はこのようになる
        ```bash
        $ curl "http://localhost:8080/getb?field_a=hello&field_b=world"
        {"a":{"FieldA":"hello"},"b":"world"}
        $ curl "http://localhost:8080/getc?field_a=hello&field_c=world"
        {"a":{"FieldA":"hello"},"c":"world"}
        $ curl "http://localhost:8080/getd?field_x=hello&field_d=world"
        {"d":"world","x":{"FieldX":"hello"}}
        ```
- HTML チェックボックスをバインドする
    - main.go
        ```go
        type myForm struct {
            Colors []string `form:"colors[]"`
        }

        ...

        func formHandler(c *gin.Context) {
            var fakeForm myForm
            c.ShouldBind(&fakeForm)
            c.JSON(200, gin.H{"color": fakeForm.Colors})
        }
        ```
    - form.html
        ```html
        <form action="/" method="POST">
            <p>Check some colors</p>
            <label for="red">Red</label>
            <input type="checkbox" name="colors[]" value="red" id="red">
            <label for="green">Green</label>
            <input type="checkbox" name="colors[]" value="green" id="green">
            <label for="blue">Blue</label>
            <input type="checkbox" name="colors[]" value="blue" id="blue">
            <input type="submit">
        </form>
        ```
    - 結果
        ```bash
        {"color":["red","green","blue"]}
        ```
- クエリ文字列 / ポストデータをバインドする
    - バインドする
        ```go
        package main

        import (
            "log"
            "time"

            "github.com/gin-gonic/gin"
        )

        type Person struct {
            Name     string    `form:"name"`
            Address  string    `form:"address"`
            Birthday time.Time `form:"birthday" time_format:"2006-01-02" time_utc:"1"`
        }

        func main() {
            route := gin.Default()
            route.GET("/testing", startPage)
            route.Run(":8085")
        }

        func startPage(c *gin.Context) {
            var person Person
            // If `GET`, only `Form` binding engine (`query`) used.
            // If `POST`, first checks the `content-type` for `JSON` or `XML`, then uses `Form` (`form-data`).
            // See more at https://github.com/gin-gonic/gin/blob/master/binding/binding.go#L48
            if c.ShouldBind(&person) == nil {
                log.Println(person.Name)
                log.Println(person.Address)
                log.Println(person.Birthday)
            }

            c.String(200, "Success")
        }
        ```
- URI をバインドする
    - URI をバインドする
        ```go
        package main

        import "github.com/gin-gonic/gin"

        type Person struct {
            ID   string `uri:"id" binding:"required,uuid"`
            Name string `uri:"name" binding:"required"`
        }

        func main() {
            route := gin.Default()
            route.GET("/:name/:id", func(c *gin.Context) {
                var person Person
                if err := c.ShouldBindUri(&person); err != nil {
                    c.JSON(400, gin.H{"msg": err})
                    return
                }
                c.JSON(200, gin.H{"name": person.Name, "uuid": person.ID})
            })
            route.Run(":8088")
        }
        ```
- テンプレートを使用して、単一のバイナリをビルドする
    - go-assets を使用すると、サードパーティのパッケージを使用して、テンプレートを含む単一のバイナリにサーバーを構築できる
        ```go
        func main() {
            r := gin.New()

            t, err := loadTemplate()
            if err != nil {
                panic(err)
            }
            r.SetHTMLTemplate(t)

            r.GET("/", func(c *gin.Context) {
                c.HTML(http.StatusOK, "/html/index.tmpl", nil)
            })
            r.Run(":8080")
        }

        // loadTemplate loads templates embedded by go-assets-builder
        func loadTemplate() (*template.Template, error) {
            t := template.New("")
            for name, file := range Assets.Files {
                if file.IsDir() || !strings.HasSuffix(name, ".tmpl") {
                    continue
                }
                h, err := ioutil.ReadAll(file)
                if err != nil {
                    return nil, err
                }
                t, err = t.New(name).Parse(string(h))
                if err != nil {
                    return nil, err
                }
            }
            return t, nil
        }
        ```
- ログ出力の色分けの制御
    - デフォルトでは、コンソールに出力されるログは、検出された TTY に応じて色分けされる
