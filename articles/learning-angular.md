---
title: "Angularを勉強していく"
emoji: "✨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [angular]
published: false
---

これからAngularを勉強してくぞー。

下記の記事を参考にしていく。
https://nextbeat-external.atlassian.net/wiki/spaces/DEV/pages/1625751900/7#Angular
https://zenn.dev/ttskch/books/84c7a272deb3845e8085

# 導入編

Angular CLIをインストール

```
$ npm install -g @angular/cli
npm WARN deprecated har-validator@5.1.5: this library is no longer supported
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142

added 239 packages, and audited 240 packages in 35s

23 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilitiesi
```

```
$ ng version

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI: 12.2.4
Node: 16.8.0 (Unsupported)
Package Manager: npm 7.21.0
OS: darwin x64

Angular: undefined
...

Package                      Version
------------------------------------------------------
@angular-devkit/architect    0.1202.4 (cli-only)
@angular-devkit/core         12.2.4 (cli-only)
@angular-devkit/schematics   12.2.4 (cli-only)
@schematics/angular          12.2.4 (cli-only)

Warning: The current version of Node (16.8.0) is not supported by Angular.
```

Angular CLIに怒られたので、

- pkjでインストールしたnodeを削除
 
 ```
 $ rm -rf /usr/local/bin/node \
   node_modules
```

- nodenvでnodeのバージョンを14.17.6に変更

```
$ nodenv local 14.17.6
$ nodenv global 14.17.6
$ nodenv versions
  10.15.0
* 14.17.6 (set by /Users/jo.harada/learning/angular/.node-version)
```

を実行した。
これで怒られなくなった。

```
$ ng version

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI: 12.2.4
Node: 14.17.6
Package Manager: npm 6.14.15
OS: darwin x64

Angular:
...

Package                      Version
------------------------------------------------------
@angular-devkit/architect    0.1202.4 (cli-only)
@angular-devkit/core         12.2.4 (cli-only)
@angular-devkit/schematics   12.2.4 (cli-only)
@schematics/angular          12.2.4 (cli-only)
```

アプリの雛形を生成する。

```
$ ng new angular-todo
? Would you like to add Angular routing? No
? Which stylesheet format would you like to use? SCSS   [ https://sass-lang.com/documentation/syntax#scss                ]
CREATE angular-todo/README.md (1057 bytes)
CREATE angular-todo/.editorconfig (274 bytes)
CREATE angular-todo/.gitignore (604 bytes)
CREATE angular-todo/angular.json (3243 bytes)
CREATE angular-todo/package.json (1074 bytes)
CREATE angular-todo/tsconfig.json (783 bytes)
CREATE angular-todo/.browserslistrc (703 bytes)
CREATE angular-todo/karma.conf.js (1429 bytes)
CREATE angular-todo/tsconfig.app.json (287 bytes)
CREATE angular-todo/tsconfig.spec.json (333 bytes)
CREATE angular-todo/src/favicon.ico (948 bytes)
CREATE angular-todo/src/index.html (297 bytes)
CREATE angular-todo/src/main.ts (372 bytes)
CREATE angular-todo/src/polyfills.ts (2820 bytes)
CREATE angular-todo/src/styles.scss (80 bytes)
CREATE angular-todo/src/test.ts (788 bytes)
CREATE angular-todo/src/assets/.gitkeep (0 bytes)
CREATE angular-todo/src/environments/environment.prod.ts (51 bytes)
CREATE angular-todo/src/environments/environment.ts (658 bytes)
CREATE angular-todo/src/app/app.module.ts (314 bytes)
CREATE angular-todo/src/app/app.component.scss (0 bytes)
CREATE angular-todo/src/app/app.component.html (24585 bytes)
CREATE angular-todo/src/app/app.component.spec.ts (974 bytes)
CREATE angular-todo/src/app/app.component.ts (217 bytes)
✔ Packages installed successfully.
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:       git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:       git branch -m <name>
    Successfully initialized git.
```

作られたディレクトリに移動し、ブランチ名をmainに変更。

```
$ cd angular-todo
$ git branch -m main
```

生成された雛形アプリを実行してみる。

```
$ ng serve --open
? Port 4200 is already in use.
Would you like to use a different port? Yes
⠋ Generating browser application bundles (phase: setup)...Compiling @angular/core : es2015 as esm2015
Compiling @angular/common : es2015 as esm2015
Compiling @angular/platform-browser : es2015 as esm2015
Compiling @angular/platform-browser-dynamic : es2015 as esm2015
✔ Browser application bundle generation complete.

Initial Chunk Files | Names         |      Size
vendor.js           | vendor        |   2.09 MB
polyfills.js        | polyfills     | 128.51 kB
main.js             | main          |  54.67 kB
runtime.js          | runtime       |   6.62 kB
styles.css          | styles        |   1.18 kB

                    | Initial Total |   2.27 MB

Build at: 2021-09-07T08:02:12.167Z - Hash: d68a26f0fe28886f0f22 - Time: 46058ms

** Angular Live Development Server is listening on localhost:58150, open your browser on http://localhost:58150/ **


✔ Compiled successfully.
✔ Browser application bundle generation complete.

5 unchanged chunks

Build at: 2021-09-07T08:02:14.965Z - Hash: 7d88cc89f9e5639fc471 - Time: 1952ms

✔ Compiled successfully.
```


## `ng serve`は何をしているか？

起点となっているのは、`angular.json`。
`angular.json`でアプリケーション全体の設定を行う。
`ng serve`は、`angular.json`で設定されている内容を元に、アプリケーションを起動する。

`angular.json`の中には、以下のような箇所がある。

```
            "index": "src/index.html",
            "main": "src/main.ts",
```

上記のより、`ng serve`すると、`src/main.ts`がエントリポイントとして読み込まれ、プログラムの実行結果が`src/index.html`にレンダリングされる。


## `main.ts`は何をしているか？

`main.ts`は簡素な内容。
ポイントは最後から２行目。

```
platformBrowserDynamic().bootstrapModule(AppModule)
```

なんとなく、**「AppModuleを」「ブラウザ環境向けに」「起動する」**というようなことをしてるっぽい。

AppModuleは、どうやら`src/app/app.comonent.ts`から`AppComponent`を読み込んで、それを起動するっぽい。

どうやら、

- `main.ts`は、`AppModule`を起動する
- `AppModule`は、`AppComponent`を読み込んでいる
- `AppComponent`は、`app.component.html`を読み込んでいる

という構造になっている。

## `index.html`には何がかkれている？

ポイントは最後から３行目の

```
  <app-root></app-root>
```

これは、`src/app/app.component.ts`の４行目。

```
  selector: 'app-root',
```

これがレンダリングの元。

## モジュールとコンポーネント

ここまでで、

1. `angular.json`に、「`src/main.ts`の実行結果を`src/index.html`にレンダリングする」、という設定が書かれている
1. `src/main.ts`は、`AppModule`を読み込んで起動している
1. `AppModule`は、`AppComponent`を読み込んで起動している
1. `AppComponent`で読み込んでいる`src/app/app.component.html`のHTMLが、`src/index.html`に埋め込まれる形でレンダリングされる

といった関係性が見えてきた。

Angularでは、アプリを構成する機能を**モジュール**という単位で分割して作成できる。
１つ以上のモジュールを組み合わせることで、アプリ全体を構成する。

`AppModule`は、アプリ起動時に最初に読み込まれる特別なモジュールで、ルートモジュールと呼ばれる。

コンポーネント
- ビュー・スタイル・ロジックをひとまとめにしたもの

コンポーネント単位で、UI部品を作っていく。

`index.html`に挿入されるコンポーネントは、ルートコンポーネントと呼ばれる。


