---
title: "Rails の学び直し: 8th: レイアウトに埋め込む"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: true
---

# 5.1 構造を追加する

## 5.1.1 ナビゲーション

レイアウトファイルを更新する。

```ruby
# app/views/layouts/application.html.erb

<!DOCTYPE html>
<html>
  <head>
    <title><%= full_title(yield(:title)) %></title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>
    <%= stylesheet_link_tag    'application', media: 'all',
                               'data-turbolinks-track': 'reload' %>
    <%= javascript_pack_tag 'application',
                               'data-turbolinks-track': 'reload' %>
    <!--[if lt IE 9]>
      <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/r29/html5.min.js">
      </script>
    <![endif]-->
  </head>
  <body>
    <header class="navbar navbar-fixed-top navbar-inverse">
      <div class="container">
        <%= link_to "sample app", '#', id: "logo" %>
        <nav>
          <ul class="nav navbar-nav navbar-right">
            <li><%= link_to "Home",   '#' %></li>
            <li><%= link_to "Help",   '#' %></li>
            <li><%= link_to "Log in", '#' %></li>
          </ul>
        </nav>
      </div>
    </header>
    <div class="container">
      <%= yield %>
    </div>
  </body>
</html>
```

また、 Home ページビューにもいくつか要素を追加する。

```ruby
# app/views/static_pages/home.html.erb

<div class="center jumbotron">
  <h1>Welcome to the Sample App</h1>

  <h2>
    This is the home page for the
    <a href="https://railstutorial.jp/">Ruby on Rails Tutorial</a>
    sample application.
  </h2>

  <%= link_to "Sign up now!", '#', class: "btn btn-lg btn-primary" %>
</div>

<%= link_to image_tag("rails.svg", alt: "Rails logo", width: "200px"),
                      "https://rubyonrails.org/" %>
```

## 5.2.2 Bootstrap とカスタム CSS

Gemfile に `bootstrap-sass` gem を追加する。

```ruby
# Gemfile

. 
.
.
gem 'bootstrap-sass', '3.4.1'
.
.
.
```

bundle install する。

```bash
$ bundle install
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies....
Using rake 12.3.3
.
.
.
Using rails 6.0.4
Installing execjs 2.8.1
Fetching autoprefixer-rails 10.4.13.0
Installing autoprefixer-rails 10.4.13.0
Fetching bootstrap-sass 3.4.1
Installing bootstrap-sass 3.4.1
Bundle complete! 25 Gemfile dependencies, 100 gems now installed.
Gems in the group 'production' were not installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

カスタム CSS ファイルを作る。

```bash
$ touch app/assets/stylesheets/custom.scss
```

`@import` で Bootstrap を読み込む。

```scss
// app/assets/stylesheets/custom.scss

@import "bootstrap-sprockets";
@import "bootstrap";
```

CSS を追加する。

```scss
// app/assets/stylesheets/custom.scss

@import "bootstrap-sprockets";
@import "bootstrap";

/* universal */

body {
  padding-top: 60px;
}

section {
  overflow: auto;
}

textarea {
  resize: vertical;
}

.center {
  text-align: center;
}

.center h1 {
  margin-bottom: 10px;
}
```

## 5.1.3 パーシャル (partial)

レイアウトにパーシャルを追加する。

```ruby
# app/views/layouts/application.html.erb

<!DOCTYPE html>
<html>
  <head>
    <title><%= full_title(yield(:title)) %></title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>
    <%= stylesheet_link_tag    'application', media: 'all',
                               'data-turbolinks-track': 'reload' %>
    <%= javascript_pack_tag 'application',
                               'data-turbolinks-track': 'reload' %>
    <%= render 'layouts/shim' %>
  </head>
  <body>
    <%= render 'layouts/header' %>
    <div class="container">
      <%= yield %>
    </div>
  </body>
</html>
```

shim パーシャルを作成する。

```ruby
# app/views/layouts/_shim.html.erb

<!--[if lt IE 9]>
  <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/r29/html5.min.js">
  </script>
<![endif]-->
```

ヘッダーのパーシャルを作成する。

```ruby
# app/views/layouts/_header.html.erb

<header class="navbar navbar-fixed-top navbar-inverse">
  <div class="container">
    <%= link_to "sample app", '#', id: "logo" %>
    <nav>
      <ul class="nav navbar-nav navbar-right">
        <li><%= link_to "Home",   '#' %></li>
        <li><%= link_to "Help",   '#' %></li>
        <li><%= link_to "Log in", '#' %></li>
      </ul>
    </nav>
  </div>
</header>
```

フッターのパーシャルを定義する。

```ruby
# app/views/layouts/_footer.html.erb

<footer class="footer">
  <small>
    The <a href="https://railstutorial.jp/">Ruby on Rails Tutorial</a>
    by <a href="https://www.michaelhartl.com/">Michael Hartl</a>
  </small>
  <nav>
    <ul>
      <li><%= link_to "About",   '#' %></li>
      <li><%= link_to "Contact", '#' %></li>
      <li><a href="https://news.railstutorial.org/">News</a></li>
    </ul>
  </nav>
</footer>
```

レイアウトにフッターを追加する。

```ruby
# app/views/layouts/application.html.erb

.
.
.
    <div class="container">
      <%= yield %>
      <!-- フッターを追加する -->
      <%= render 'layouts/footer' %>
    </div>
.
.
.
```

フッター用の CSS を追加する。

```scss
// app/assets/stylesheets/custom.scss

.
.
.
/* footer */

footer {
  margin-top: 45px;
  padding-top: 5px;
  border-top: 1px solid #eaeaea;
  color: #777;
}

footer a {
  color: #555;
}

footer a:hover {
  color: #222;
}

footer small {
  float: left;
}

footer ul {
  float: right;
  list-style: none;
}

footer ul li {
  float: left;
  margin-left: 15px;
}
```

### 演習

#### 1.

レイアウトで共通パーシャルを読み込む。

```ruby
# app/views/layouts/application.html.erb

  <head>
    <title><%= full_title(yield(:title)) %></title>
    <!-- 共通パーシャルを使用する -->
    <%= render 'layouts/rails_default' %>
    <%= render 'layouts/shim' %>
  </head>
```

#### 2.

テストを実行する。

```bash
$ bundle exec guard
20:01:54 - INFO - Guard::Minitest 2.4.6 is running, with Minitest::Unit 5.11.3!
20:01:54 - INFO - Guard is now watching at '/Volumes/dev/git-dev/rails/sample_app'
[1] guard(main)>
20:04:57 - INFO - Run all
20:04:57 - INFO - Running: all tests
Running via Spring preloader in process 9646
Started with run options --seed 36189

ERROR["test_should_get_help", #<Minitest::Reporters::Suite:0x00007fa1d437dbd8 @name="StaticPagesControllerTest">, 0.08896700013428926]
 test_should_get_help#StaticPagesControllerTest (0.09s)
ActionView::Template::Error:         ActionView::Template::Error: Missing partial layouts/_rails_default with {:locale=>[:en], :formats=>[:html], :variants=>[], :handlers=>[:raw, :erb, :html, :builder, :ruby, :jbuilder]}. Searched in:
          * "/Volumes/dev/git-dev/rails/sample_app/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actiontext-6.0.4/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actionmailbox-6.0.4/app/views"

            app/views/layouts/application.html.erb:5
            test/controllers/static_pages_controller_test.rb:21:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_contact", #<Minitest::Reporters::Suite:0x00007fa1d4348fc8 @name="StaticPagesControllerTest">, 0.09061400010250509]
 test_should_get_contact#StaticPagesControllerTest (0.09s)
ActionView::Template::Error:         ActionView::Template::Error: Missing partial layouts/_rails_default with {:locale=>[:en], :formats=>[:html], :variants=>[], :handlers=>[:raw, :erb, :html, :builder, :ruby, :jbuilder]}. Searched in:
          * "/Volumes/dev/git-dev/rails/sample_app/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actiontext-6.0.4/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actionmailbox-6.0.4/app/views"

            app/views/layouts/application.html.erb:5
            test/controllers/static_pages_controller_test.rb:33:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_about", #<Minitest::Reporters::Suite:0x00007fa1d4311898 @name="StaticPagesControllerTest">, 0.0916399999987334]
 test_should_get_about#StaticPagesControllerTest (0.09s)
ActionView::Template::Error:         ActionView::Template::Error: Missing partial layouts/_rails_default with {:locale=>[:en], :formats=>[:html], :variants=>[], :handlers=>[:raw, :erb, :html, :builder, :ruby, :jbuilder]}. Searched in:
          * "/Volumes/dev/git-dev/rails/sample_app/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actiontext-6.0.4/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actionmailbox-6.0.4/app/views"

            app/views/layouts/application.html.erb:5
            test/controllers/static_pages_controller_test.rb:27:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_home", #<Minitest::Reporters::Suite:0x00007fa1e72e8bb0 @name="StaticPagesControllerTest">, 0.8158300002105534]
 test_should_get_home#StaticPagesControllerTest (0.82s)
ActionView::Template::Error:         ActionView::Template::Error: Missing partial layouts/_rails_default with {:locale=>[:en], :formats=>[:html], :variants=>[], :handlers=>[:raw, :erb, :html, :builder, :ruby, :jbuilder]}. Searched in:
          * "/Volumes/dev/git-dev/rails/sample_app/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actiontext-6.0.4/app/views"
          * "/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/actionmailbox-6.0.4/app/views"

            app/views/layouts/application.html.erb:5
            test/controllers/static_pages_controller_test.rb:15:in `block in <class:StaticPagesControllerTest>'

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.83957s
4 tests, 0 assertions, 0 failures, 4 errors, 0 skips

[1] guard(main)>
```

#### 3.

`head` タグの共通パーシャルを作成する。

```ruby
# app/views/layouts/_rails_default.html.erb

<%= csrf_meta_tags %>
<%= csp_meta_tag %>
<%= stylesheet_link_tag 'application', media: 'all',
                        'data-turbolinks-track': 'reload' %>
<%= javascript_pack_tag 'application',
                        'data-turbolinks-track': 'reload' %>
```

テストを実行する。

```bash
[1] guard(main)>
20:08:06 - INFO - Run all
20:08:06 - INFO - Running: all tests
Running via Spring preloader in process 27933
Started with run options --seed 40267

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.90422s
4 tests, 8 assertions, 0 failures, 0 errors, 0 skips

[1] guard(main)>
```

# 5.2 Sass とアセットパイプライン

## 5.2.1 アセットパイプライン

### アセットディレクトリ

下記のディレクトリが使われる。

- `app/assets`
- `lib/assets`
- `vendor/assets`

### マニフェストファイル

例えば、 CSS 用のマニフェストファイルは `app/assets/stylesheets/application.css` で定義する。

### プリプロセッサエンジン

Rails では、ファイル名の拡張子によって、どのプリプロセッサエンジンを使うかを判断する。
例えば、 `foobar.js.erb` の場合、 `.erb` が最初に実行され、生成されたファイルを JavaScript のコードとして結合する。

### 本番環境での効率性

アセットパイプラインの最大のメリットの1つは、本番のアプリケーションで効率的になるように最適化されたアセットも自動的に生成されること。

## 5.2.2 素晴らしい構文を備たスタイルシート

### ネスト

共通のパターンがある場合、要素をネストできる。

```scss
// 元のコード
.center {
  text-align: center;
}

.center h1 {
  margin-bottom: 10px;
}

// .center でネストできる
.center {
  text-align: center;
  h1 {
    margin-bottom: 10px;
  }
}
```

親属性を参照する場合は `&` を使う。

```scss
// 元のコード
#logo {
  float: left;
  margin-right: 10px;
  font-size: 1.7em;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: -1px;
  padding-top: 9px;
  font-weight: bold;
}

#logo:hover {
  color: #fff;
  text-decoration: none;
}

// #logo でネストできる
#logo {
  float: left;
  margin-right: 10px;
  font-size: 1.7em;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: -1px;
  padding-top: 9px;
  font-weight: bold;
  &:hover {
    color: #fff;
    text-decoration: none;
  }
}
```

### 変数

冗長なコードを削除し、より自由な表現を可能にするため、 `変数` を定義できる。

```scss
// 元のコード
h2 {
  .
  .
  .
  color: #777;
}
.
.
.
footer {
  .
  .
  .
  color: #777;
}

// 変数を定義する
$light-gray: #777;
.
.
.
h2 {
  .
  .
  .
  color: $light-gray;
}
.
.
.
footer {
  .
  .
  .
  color: $light-gray;
}
```

# 5.3 レイアウトのリンク

下記のようにリンクを直接記述することもできるが、 Rails 竜ではない。

```ruby
<a href="/static_pages/about">About</a>
```

Rails では `名前付きルート` を使うのが慣例となっている。

```ruby
<%= link_to "About", about_path %>
```

`about_path` の定義を変えれば URL を変更できるので、柔軟性が高まる。

## 5.3.1 Contact ページ

演習で既に実装済みのため、スキップ。

## 5.3.2 Rails のルート URL

ルート URL を定義すると、下記のメソッドで URL を参照できる。

- `root_path`: ルート URL 以下の文字列を返す
- `root_url`: 完全な URL の文字列を返す。

```
root_path -> '/'
root_url  -> 'https://www.example.com/'
```

Rails では基本的に `_path` 書式を使い、リダイレクトの場合のみ `_url` 書式を使う。

`get` ルールで名前付きルートを使う。

```ruby
# 元のルーティング
get 'static_pages/help'

# 名前付きルートを使う
get 'help', to: 'static_pages#help'
```

ルーティングを名前付きルートを使って定義し直す。

```ruby
# config/routes.rb

Rails.application.routes.draw do
  root 'static_pages#home'
  get '/helop',   to: 'static_pages#help'
  get '/about',   to: 'static_pages#about'
  get '/contact', to: 'static_pages#contact'
end
```

テストを実行する。

```bash
09:13:01 - INFO - Running: test/controllers//static_pages_controller_test.rb
Running via Spring preloader in process 32283
Started with run options --seed 5667

ERROR["test_should_get_help", #<Minitest::Reporters::Suite:0x00007fdfa45ebd30 @name="StaticPagesControllerTest">, 0.05688600009307265]
 test_should_get_help#StaticPagesControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `static_pages_help_url' for #<StaticPagesControllerTest:0x00007fdfa45f8288>
            test/controllers/static_pages_controller_test.rb:21:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_home", #<Minitest::Reporters::Suite:0x00007fdfa45dacd8 @name="StaticPagesControllerTest">, 0.058307000203058124]
 test_should_get_home#StaticPagesControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `static_pages_home_url' for #<StaticPagesControllerTest:0x00007fdfa45f8288>
            test/controllers/static_pages_controller_test.rb:15:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_contact", #<Minitest::Reporters::Suite:0x00007fdfa45d0ad0 @name="StaticPagesControllerTest">, 0.05869600013829768]
 test_should_get_contact#StaticPagesControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `static_pages_contact_url' for #<StaticPagesControllerTest:0x00007fdfa45f8288>
            test/controllers/static_pages_controller_test.rb:33:in `block in <class:StaticPagesControllerTest>'

ERROR["test_should_get_about", #<Minitest::Reporters::Suite:0x00007fdfa45c38d0 @name="StaticPagesControllerTest">, 0.05893800011835992]
 test_should_get_about#StaticPagesControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `static_pages_about_url' for #<StaticPagesControllerTest:0x00007fdfa45f8288>
            test/controllers/static_pages_controller_test.rb:27:in `block in <class:StaticPagesControllerTest>'

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.09821s
4 tests, 0 assertions, 0 failures, 4 errors, 0 skips
```

テストを修正する。

```ruby
# test/controllers/static_pages_controller_test.rb

class StaticPagesControllerTest < ActionDispatch::IntegrationTest
  .
  .
  .
  test "should get home" do
    get root_path
    .
    .
    .
  end

  test "should get help" do
    get help_path
    .
    .
    .
  end

  test "should get about" do
    get about_path
    .
    .
    .
  end

  test "should get contact" do
    get contact_path
    .
    .
    .
  end
end
```

テストを実行する。

```bash
09:17:35 - INFO - Run all
09:17:35 - INFO - Running: all tests
Running via Spring preloader in process 58351
Started with run options --seed 52607

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.92602s
4 tests, 8 assertions, 0 failures, 0 errors, 0 skips
```

### 演習

#### 1.

`as:` オプションを使って、 Help ページの名前付きルートを `helf` に変更する。

```ruby
# config/routes.rb

  get '/help',    to: 'static_pages#help',   as: 'helf'
```

#### 2.

先程の変更により、テストが `RED` となる。

```bash
09:19:06 - INFO - Running: test/controllers//static_pages_controller_test.rb
Running via Spring preloader in process 67078
Started with run options --seed 64961

ERROR["test_should_get_help", #<Minitest::Reporters::Suite:0x00007fbe05c3f800 @name="StaticPagesControllerTest">, 0.060252000112086535]
 test_should_get_help#StaticPagesControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `help_path' for #<StaticPagesControllerTest:0x00007fbe05c4c438>
            test/controllers/static_pages_controller_test.rb:21:in `block in <class:StaticPagesControllerTest>'

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.88409s
4 tests, 6 assertions, 0 failures, 1 errors, 0 skips
```

ルーティングを変更する。

```ruby
# test/controllers/static_pages_controller_test.rb

  test "should get help" do
    get helf_path
```

テストが `GREEN` となる。

```bash
09:21:29 - INFO - Running: test/controllers/static_pages_controller_test.rb
Running via Spring preloader in process 81181
Started with run options --seed 43102

  4/4: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.91977s
4 tests, 8 assertions, 0 failures, 0 errors, 0 skips
```

#### 3.

上記の変更をもとに戻す。


## 5.3.3 名前付きルート

`link_to` メソッドの2番めの引数に、適切な名前付きルートを使う。

```ruby
# 元のコード
<%= link_to "About", '#' %>

# 名前付きルートを使う
<%= link_to "About", about_path %>
```

まず、 header パーシャルのリンクを変更する。

```ruby
# app/views/layouts/_header.html.erb

    <%= link_to "sample app", root_path, id: "logo" %>
    <nav>
      <ul class="nav navbar-nav navbar-right">
        <li><%= link_to "Home",   root_path %></li>
        <li><%= link_to "Help",   help_path %></li>
```

footer パーシャルのリンクも変更する。

```ruby
# app/views/layouts/_footer.html.erb

      <li><%= link_to "About",   about_path %></li>
      <li><%= link_to "Contact", contact_path %></li>
```


## 5.3.4 リンクのテスト

`統合テスト ( *Integration Test* )` を導入するため、 `site_layout` とうテストのテンプレートを生成する。

```bash
$ rails generate integration_test site_layout
Running via Spring preloader in process 39064
      invoke  test_unit
      create    test/integration/site_layout_test.rb
```

レイアウトの各リンクが正しく動くかどうかチェックする。

1. ルート URL (Home ページ) に GET リクエストを送る
2. 正しいページテンプレートが描画されているかどうか確かめる
3. Home, Help, About, Contact の各ページへのリンクが正しく動くか確かめる

`assert_template` メソッドを使って、 Home ページが正しいビューを描画しているかどうか確かめる。

```ruby
# test/integration/site_layout_test.rb

require 'test_helper'

class SiteLayoutTest < ActionDispatch::IntegrationTest

  test "layout links" do
    get root_path
    assert_template 'static_pages/home'
    assert_select "a[href=?]", root_path, count: 2
    assert_select "a[href=?]", help_path
    assert_select "a[href=?]", about_path
    assert_select "a[href=?]", contact_path
  end
end
```

`assert_select` は柔軟でパワフルな機能だが、HTML 要素 (リンクなど) をテストするぐらいに抑えた方が良い。

統合テストは下記コマンドで実行できる。

```bash
rails test:integration
Started with run options --seed 42836

  1/1: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:01, Time: 00:00:01

Finished in 1.06143s
1 tests, 5 assertions, 0 failures, 0 errors, 0 skips
```

全てのテストを実行してみる。

```bash
rails test
Running via Spring preloader in process 96153
Started with run options --seed 59605

  5/5: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.94059s
5 tests, 13 assertions, 0 failures, 0 errors, 0 skips
```

### 演習

#### 1.

footer パーシャルのリンクを変更してみる。

```ruby
# app/views/layouts/_footer.html.erb
      <li><%= link_to "About",   contact_path %></li>
```

テストを実行してみると、エラーを捕捉できていることがわかる。

```bash
rails test
Running via Spring preloader in process 1358
Started with run options --seed 13906

 FAIL["test_layout_links", #<Minitest::Reporters::Suite:0x00007f84708a30d0 @name="SiteLayoutTest">, 0.9059540000744164]
 test_layout_links#SiteLayoutTest (0.91s)
        Expected at least 1 element matching "a[href=\"/about\"]", found 0.
        Expected 0 to be >= 1.
        test/integration/site_layout_test.rb:10:in `block in <class:SiteLayoutTest>'

  5/5: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.98564s
5 tests, 12 assertions, 1 failures, 0 errors, 0 skips
```

#### 2.

test 環境でも Application ヘルパーを使えるようにする。

```ruby
# test/test_helper.rb
class ActiveSupport::TestCase
  .
  .
  .
  include ApplicationHelper
end
```

テストで `full_title` メソッドを使ってみる。

```ruby
# test/integration/site_layout_test.rb

  test "layout links" do
    .
    .
    .
    get contact_path
    assert_select "title", full_title("Contact")
  end
```

`full_title` メソッドの単体テストを作成する。

```ruby
# test/helpers/application_helper_test.rb

require 'test_helper'

class ApplicationHelperTest < ActionView::TestCase
  test "full title helper" do
    assert_equal full_title,         "Ruby on Rails Tutorial Sample App"
    assert_equal full_title("Help"), "Help | Ruby on Rails Tutorial Sample App"
  end
end
```

テストを実行する。

```bash
$ rails test
Running via Spring preloader in process 4681
Started with run options --seed 30927

  6/6: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.94624s
6 tests, 16 assertions, 0 failures, 0 errors, 0 skips
```

# 5.4 ユーザー登録: 最初のステップ

## 5.4.1 Users コントローラ

新規ユーザー用のユーザー登録ページ向けのコントローラを作成する。

```bash
$ rails generate controller Users new
Running via Spring preloader in process 40757
      create  app/controllers/users_controller.rb
       route  get 'users/new'
      invoke  erb
      create    app/views/users
      create    app/views/users/new.html.erb
      invoke  test_unit
      create    test/controllers/users_controller_test.rb
      invoke  helper
      create    app/helpers/users_helper.rb
      invoke    test_unit
      invoke  assets
      invoke    scss
      create      app/assets/stylesheets/users.scss
```

上記により、Users コントローラとユーザービュー、テストが作成される。

```ruby
# app/controllers/users_controller.rb

class UsersController < ApplicationController
  def new
  end
end
```

```ruby
# app/views/users/new.html.erb

<h1>Users#new</h1>
<p>Find me in app/views/users/new.html.erb</p>
```

```ruby
# test/controllers/users_controller_test.rb

require 'test_helper'

class UsersControllerTest < ActionDispatch::IntegrationTest
  test "should get new" do
    get users_new_url
    assert_response :success
  end

end
```

テストがパスすることを確認する。

```bash
$ rails test
Running via Spring preloader in process 58489
Started with run options --seed 42516

  7/7: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:02, Time: 00:00:02

Finished in 2.88587s
7 tests, 17 assertions, 0 failures, 0 errors, 0 skips
```

### 演習

#### 1.

ルーティングで `signup_path` を定義する。

```ruby
# config/routes.rb

Rails.application.routes.draw do
  .
  .
  .
  get '/signup',  to: 'users#new'
end
```

#### 2.

テストを実行する。

```bash
$ rails test
Running via Spring preloader in process 86938
Started with run options --seed 48772

ERROR["test_should_get_new", #<Minitest::Reporters::Suite:0x00007f9fd59daf18 @name="UsersControllerTest">, 0.058170000091195107]
 test_should_get_new#UsersControllerTest (0.06s)
NameError:         NameError: undefined local variable or method `users_new_url' for #<UsersControllerTest:0x00007f9fd5a09ae8>
            test/controllers/users_controller_test.rb:5:in `block in <class:UsersControllerTest>'

  7/7: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.92062s
7 tests, 16 assertions, 0 failures, 1 errors, 0 skips
```

テストで `signup_path` を使用する。

```ruby
# test/controllers/users_controller_test.rb

  test "should get new" do
    get signup_path
    assert_response :success
  end
```

再度テストを実行する。

```bash
rails test
Running via Spring preloader in process 81632
Started with run options --seed 33177

  7/7: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 0.93784s
7 tests, 17 assertions, 0 failures, 0 errors, 0 skips
```


## 5.4.2 ユーザー登録用 URL

ユーザー登録 URL ように `get '/signup'` のルーティングを追加する。

```ruby
# config/routes.rb

Rails.application.routes.draw do
  .
  .
  .
  get '/signup',  to: 'users#new'
end
```

テストを修正する。

```ruby
# test/controllers/users_controller_test.rb

  test "should get new" do
    get signup_path
    assert_response :success
  end
```

Home ページのボタンに `signup_path` を追加する。

```ruby
# app/views/static_pages/home.html.erb

  <%= link_to "Sign up now!", signup_path, class: "btn btn-lg btn-primary" %>
```

最後に、signup ページ用のカスタムスタブのビューを追加する。

```ruby
# app/views/users/new.html.erb

<% provide(:title, 'Sign up') %>
<h1>Sign up</h1>
<p>This will be a signup page for new users.</p>
```

### 演習

#### 1.

`signup_path` は実装済みのため、スキップ。

#### 2.

こちらも同様にスキップ。

#### 3.

統合テストに Sign up ページでのテストを追加する。

```ruby
# test/integration/site_layout_test.rb

  test "layout links" do
    .
    .
    .
    get signup_path
    assert_select "title", full_title("Sign up")
  end
```

テストを実行する。

```bash
$ rails test
Running via Spring preloader in process 85774
Started with run options --seed 22524

  7/7: [===================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:01, Time: 00:00:01

Finished in 1.06477s
7 tests, 18 assertions, 0 failures, 0 errors, 0 skips
```

# 5.5 最後に

## 5.5.1 本章のまとめ

- HTML5 を使って header や footer、 logo や body といったコンテンツのレイアウトを定義した
- Rails のパーシャルは効率化のために使われ、別ファイルにマークアップを切り出すことができる
- CSS は、 CSS クラスと id を使ってレイアウトやデザインを調整する
- Bootstrap フレームワークを使うと、いい感じのデザインを素早く実装できる
- Sass と Asset Pipeline は、(開発効率のために切り分けられた) CSS の冗長な部分を圧縮し、本番環境に最適化した結果を出力する
- Rails のルーティングでは自由にルールを定義することができ、また、その際に名前付きルートも使えるようになる
- 統合テストは、ブラウザによるページ間の遷移を効率的にシミュレートする
