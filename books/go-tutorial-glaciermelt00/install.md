
reference: https://go.dev/doc/manage-install

```
// .zshrc
# Go
export PATH=$(go env GOPATH)/bin:$PATH
```

```bash
$ go install golang.org/dl/go1.20.5@latest
go: downloading golang.org/dl v0.0.0-20230621153230-07a9d2000df2

$ go1.20.5 download
Downloaded   0.0% (    16384 / 100202970 bytes) ...
Downloaded   1.7% (  1703936 / 100202970 bytes) ...
Downloaded  17.0% ( 17072000 / 100202970 bytes) ...
Downloaded  30.3% ( 30342944 / 100202970 bytes) ...
Downloaded  44.6% ( 44695216 / 100202970 bytes) ...
Downloaded  58.1% ( 58211920 / 100202970 bytes) ...
Downloaded  72.4% ( 72580576 / 100202970 bytes) ...
Downloaded  84.5% ( 84721024 / 100202970 bytes) ...
Downloaded  98.1% ( 98319648 / 100202970 bytes) ...
Downloaded 100.0% (100202970 / 100202970 bytes)
Unpacking /Users/glaciermelt/sdk/go1.20.5/go1.20.5.darwin-amd64.tar.gz ...
Success. You may now run 'go1.20.5'

$ go1.20.5 version
go version go1.20.5 darwin/amd64

$ go1.20.5 env GOROOT
/Users/glaciermelt/sdk/go1.20.5

$ go install -v golang.org/x/tools/gopls@latest
go: downloading golang.org/x/tools/gopls v0.12.4
go: downloading golang.org/x/tools v0.10.0
go: downloading golang.org/x/tools v0.10.1-0.20230622221742-0622ad2359a7
go: downloading github.com/sergi/go-diff v1.1.0
go: downloading honnef.co/go/tools v0.4.2
go: downloading mvdan.cc/gofumpt v0.4.0
go: downloading mvdan.cc/xurls/v2 v2.4.0
go: downloading golang.org/x/mod v0.11.0
go: downloading golang.org/x/sync v0.3.0
go: downloading golang.org/x/text v0.10.0
go: downloading golang.org/x/exp/typeparams v0.0.0-20221212164502-fae10dda9338
go: downloading github.com/google/go-cmp v0.5.9
go: downloading golang.org/x/sys v0.9.0
go: downloading golang.org/x/exp v0.0.0-20220722155223-a9213eeb770e
go: downloading golang.org/x/vuln v0.0.0-20230110180137-6ad3e3d07815
go: downloading github.com/BurntSushi/toml v1.2.1
```
