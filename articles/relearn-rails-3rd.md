---
title: "Rails の学び直し: 3rd"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# hello_app: Bundler

## Gemfile

```bash
$ bundle _2.2.17_ install
Fetching gem metadata from https://rubygems.org/...........
You have requested:
  listen = 3.1.5

The bundle currently has listen locked at 3.8.0.
Try running `bundle update listen`

If you are updating multiple gems in your Gemfile at once,
try passing them all to `bundle update`

// bundle を update する
$ bundle update
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies.....
Fetching rake 12.3.3 (was 13.0.6)
Installing rake 12.3.3 (was 13.0.6)
Using concurrent-ruby 1.2.2
Using minitest 5.18.1
Using rack 2.2.7
Using mini_mime 1.1.2
Using date 3.3.3
Using timeout 0.4.0
Using public_suffix 5.0.3
Using crass 1.0.6
Using msgpack 1.7.1
Using bundler 2.2.17
Using marcel 1.0.2
Using thread_safe 0.3.6
Using zeitwerk 2.6.8
Using ffi 1.15.5
Using rb-fsevent 0.11.2
Using builder 3.2.4
Using method_source 1.0.0
Using thor 1.2.2
Using websocket-extensions 0.1.5
Fetching ruby_dep 1.5.0
Fetching childprocess 2.0.0
Fetching byebug 11.0.1 (was 11.1.3)
Fetching regexp_parser 1.8.2 (was 2.8.1)
Fetching rubyzip 1.3.0 (was 2.3.2)
Using bindex 0.8.1
Using nio4r 2.5.9
Fetching sqlite3 1.4.2 (was 1.6.3)
Using tilt 2.2.0
Using turbolinks-source 5.2.0
Using i18n 1.14.1
Using rack-test 2.1.0
Using rack-proxy 0.7.6
Fetching sprockets 3.7.2 (was 4.2.0)
Using erubi 1.12.0
Using net-protocol 0.2.1
Using addressable 2.8.4
Fetching bootsnap 1.10.3 (was 1.16.0)
Fetching spring 2.1.0 (was 2.1.1)
Using racc 1.7.1
Using tzinfo 1.2.11
Using rb-inotify 0.10.1
Using websocket-driver 0.7.5
Fetching puma 4.3.6 (was 4.3.12)
Installing ruby_dep 1.5.0
Installing childprocess 2.0.0 with native extensions
Installing spring 2.1.0 (was 2.1.1)
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Fetching turbolinks 5.2.0 (was 5.2.1)
Installing byebug 11.0.1 (was 11.1.3) with native extensions
Installing sqlite3 1.4.2 (was 1.6.3) with native extensions
Installing regexp_parser 1.8.2 (was 2.8.1)
Installing bootsnap 1.10.3 (was 1.16.0) with native extensions
Installing turbolinks 5.2.0 (was 5.2.1)
Installing sprockets 3.7.2 (was 4.2.0)
Installing rubyzip 1.3.0 (was 2.3.2)
Installing puma 4.3.6 (was 4.3.12) with native extensions
Using activesupport 6.0.4 (was 6.0.6.1)
Using nokogiri 1.15.3 (x86_64-darwin)
Using mail 2.8.1
Using rails-dom-testing 2.1.1
Using loofah 2.21.3
Using globalid 1.1.0
Using activemodel 6.0.4 (was 6.0.6.1)
Using xpath 3.2.0
Using rails-html-sanitizer 1.6.0
Using activejob 6.0.4 (was 6.0.6.1)
Using activerecord 6.0.4 (was 6.0.6.1)
Using actionview 6.0.4 (was 6.0.6.1)
Using actionpack 6.0.4 (was 6.0.6.1)
Using actioncable 6.0.4 (was 6.0.6.1)
Using activestorage 6.0.4 (was 6.0.6.1)
Using actionmailer 6.0.4 (was 6.0.6.1)
Using railties 6.0.4 (was 6.0.6.1)
Using sprockets-rails 3.4.2
Using actionmailbox 6.0.4 (was 6.0.6.1)
Using actiontext 6.0.4 (was 6.0.6.1)
Using rails 6.0.4 (was 6.0.6.1)
Fetching sass-listen 4.0.0
Fetching listen 3.1.5 (was 3.8.0)
Installing listen 3.1.5 (was 3.8.0)
Installing sass-listen 4.0.0
Using spring-watcher-listen 2.0.1
Fetching web-console 4.0.1 (was 4.2.0)
Fetching jbuilder 2.9.1 (was 2.11.5)
Installing web-console 4.0.1 (was 4.2.0)
Installing jbuilder 2.9.1 (was 2.11.5)
Fetching webpacker 4.0.7 (was 4.3.0)
Fetching selenium-webdriver 3.142.4 (was 4.9.0)
Fetching sass 3.7.4
Fetching capybara 3.28.0 (was 3.39.2)
Installing webpacker 4.0.7 (was 4.3.0)
Installing sass 3.7.4
Installing capybara 3.28.0 (was 3.39.2)
Installing selenium-webdriver 3.142.4 (was 4.9.0)
Fetching sass-rails 5.1.0 (was 6.0.0)
Installing sass-rails 5.1.0 (was 6.0.0)
Fetching webdrivers 4.1.2 (was 5.2.0)
Installing webdrivers 4.1.2 (was 5.2.0)
Bundle updated!
Post-install message from sass:

Ruby Sass has reached end-of-life and should no longer be used.

* If you use Sass as a command-line tool, we recommend using Dart Sass, the new
  primary implementation: https://sass-lang.com/install

* If you use Sass as a plug-in for a Ruby web framework, we recommend using the
  sassc gem: https://github.com/sass/sassc-ruby#readme

* For more details, please refer to the Sass blog:
  https://sass-lang.com/blog/posts/7828841

// bundle を install する
$ bundle _2.2.17_ install
Using rake 12.3.3
Using concurrent-ruby 1.2.2
Using i18n 1.14.1
Using minitest 5.18.1
Using thread_safe 0.3.6
Using tzinfo 1.2.11
Using zeitwerk 2.6.8
Using activesupport 6.0.4
Using builder 3.2.4
Using erubi 1.12.0
Using racc 1.7.1
Using nokogiri 1.15.3 (x86_64-darwin)
Using rails-dom-testing 2.1.1
Using crass 1.0.6
Using loofah 2.21.3
Using rails-html-sanitizer 1.6.0
Using actionview 6.0.4
Using rack 2.2.7
Using rack-test 2.1.0
Using actionpack 6.0.4
Using nio4r 2.5.9
Using websocket-extensions 0.1.5
Using websocket-driver 0.7.5
Using actioncable 6.0.4
Using globalid 1.1.0
Using activejob 6.0.4
Using activemodel 6.0.4
Using activerecord 6.0.4
Using marcel 1.0.2
Using activestorage 6.0.4
Using mini_mime 1.1.2
Using date 3.3.3
Using timeout 0.4.0
Using net-protocol 0.2.1
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using mail 2.8.1
Using actionmailbox 6.0.4
Using actionmailer 6.0.4
Using actiontext 6.0.4
Using public_suffix 5.0.3
Using addressable 2.8.4
Using bindex 0.8.1
Using msgpack 1.7.1
Using bootsnap 1.10.3
Using bundler 2.2.17
Using byebug 11.0.1
Using regexp_parser 1.8.2
Using xpath 3.2.0
Using capybara 3.28.0
Using childprocess 2.0.0
Using ffi 1.15.5
Using jbuilder 2.9.1
Using rb-fsevent 0.11.2
Using rb-inotify 0.10.1
Using ruby_dep 1.5.0
Using listen 3.1.5
Using method_source 1.0.0
Using puma 4.3.6
Using rack-proxy 0.7.6
Using thor 1.2.2
Using railties 6.0.4
Using sprockets 3.7.2
Using sprockets-rails 3.4.2
Using rails 6.0.4
Using rubyzip 1.3.0
Using sass-listen 4.0.0
Using sass 3.7.4
Using tilt 2.2.0
Using sass-rails 5.1.0
Using selenium-webdriver 3.142.4
Using spring 2.1.0
Using spring-watcher-listen 2.0.1
Using sqlite3 1.4.2
Using turbolinks-source 5.2.0
Using turbolinks 5.2.0
Using web-console 4.0.1
Using webdrivers 4.1.2
Using webpacker 4.0.7
Bundle complete! 17 Gemfile dependencies, 80 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

## Webpacker をインストールする

```bash
$ ails webpacker:install
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
RAILS_ENV=development environment is not defined in config/webpacker.yml, falling back to production environment
      create  config/webpacker.yml
Copying webpack core config

...

├ toidentifier@1.0.1
├ utils-merge@1.0.1
├ uuid@8.3.2
├ wbuf@1.7.3
├ webpack-dev-middleware@5.3.3
├ webpack-dev-server@4.15.1
├ websocket-driver@0.7.4
├ websocket-extensions@0.1.4
└ ws@8.13.0
✨  Done in 5.94s.
Webpacker successfully installed 🎉 🍰
```

## ローカル Web サーバーへの接続設定

```ruby
# config/environments/development.rb

Rails.application.configure do

  ...

  # Cloud9 への接続を許可する
  config.hosts.clear
end
```

## Rails サーバーを実行する

```bash
$ rails server
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
=> Booting Puma
=> Rails 6.0.4 application starting in development
=> Run `rails server --help` for more startup options
Puma starting in single mode...
* Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
* Min threads: 5, max threads: 5
* Environment: development
* Listening on tcp://127.0.0.1:3000
* Listening on tcp://[::1]:3000
Use Ctrl-C to stop
```

loaclhost:3000 にアクセスすると、実行されていることが確認できる。

## コントローラに hello 関数を追加

```ruby
# app/controllers/application_controller.rb

class ApplicationController < ActionController::Base

  def hello
    render html: "hello, world!"
  end
end
```

## ルーティングを追加

```ruby
# config/routes.rb

Rails.application.routes.draw do
  root 'application#hello'
end
```

# デプロイ

## Gemfile

Heroku で PostgreSQL データベースを使用するため、 `pg`` gem を追加する。

```ruby
# Gemfile

group :production do
  gem 'pg', '1.1.4'
end
```

## bundle 設定

```bash
// bundle config
$ bundle _2.2.17_ config set --local without 'production'
$ bundle _2.2.17_ config
Settings are listed in order of priority. The top value will be used.
build.puma
Set for your local app (/Volumes/dev/git-dev/rails/hello_app/.bundle/config): "--with-opt-dir=/usr/local/Cellar/openssl@3/3.1.1_1"
Set for the current user (/Users/glaciermelt/.bundle/config): "--with-cflags=-Wno-error=implicit-function-declaration"

without
Set for your local app (/Volumes/dev/git-dev/rails/hello_app/.bundle/config): [:production]

// bundle install
$ bundle _2.2.17_ install
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies...
Using rake 12.3.3
Using concurrent-ruby 1.2.2
Using minitest 5.18.1
Using thread_safe 0.3.6
Using erubi 1.12.0
Using nio4r 2.5.9
Using timeout 0.4.0
Using crass 1.0.6
Using bindex 0.8.1
Using zeitwerk 2.6.8
Using msgpack 1.7.1
Using byebug 11.0.1
Using regexp_parser 1.8.2
Using childprocess 2.0.0
Using ffi 1.15.5
Using rb-fsevent 0.11.2
Using public_suffix 5.0.3
Using ruby_dep 1.5.0
Using thor 1.2.2
Using websocket-extensions 0.1.5
Using tilt 2.2.0
Using mini_mime 1.1.2
Using sqlite3 1.4.2
Using builder 3.2.4
Using i18n 1.14.1
Using tzinfo 1.2.11
Using puma 4.3.6
Using bundler 2.2.17
Using net-protocol 0.2.1
Using bootsnap 1.10.3
Using rb-inotify 0.10.1
Using websocket-driver 0.7.5
Using activesupport 6.0.4
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using listen 3.1.5
Using sass-listen 4.0.0
Using globalid 1.1.0
Using rubyzip 1.3.0
Using jbuilder 2.9.1
Using marcel 1.0.2
Using activejob 6.0.4
Using sass 3.7.4
Using selenium-webdriver 3.142.4
Using activemodel 6.0.4
Using spring 2.1.0
Using turbolinks-source 5.2.0
Using racc 1.7.1
Using activerecord 6.0.4
Using spring-watcher-listen 2.0.1
Using turbolinks 5.2.0
Using method_source 1.0.0
Using rack 2.2.7
Using nokogiri 1.15.3 (x86_64-darwin)
Using addressable 2.8.4
Using rack-test 2.1.0
Using sprockets 3.7.2
Using date 3.3.3
Using rails-dom-testing 2.1.1
Using rack-proxy 0.7.6
Using net-imap 0.3.6
Using xpath 3.2.0
Using webdrivers 4.1.2
Using loofah 2.21.3
Using mail 2.8.1
Using capybara 3.28.0
Using rails-html-sanitizer 1.6.0
Using actionview 6.0.4
Using actionpack 6.0.4
Using actioncable 6.0.4
Using activestorage 6.0.4
Using actionmailer 6.0.4
Using railties 6.0.4
Using sprockets-rails 3.4.2
Using actionmailbox 6.0.4
Using actiontext 6.0.4
Using sass-rails 5.1.0
Using web-console 4.0.1
Using webpacker 4.0.7
Using rails 6.0.4
Bundle complete! 18 Gemfile dependencies, 80 gems now installed.
Gems in the group 'production' were not installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

## Heroku がインストールされているか確認

```bash
$ heroku --version
/usr/local/Cellar/heroku/8.1.9/libexec/bin/node: --openssl-legacy-provider is not allowed in NODE_OPTIONS

// NODE_OPTIONS を削除する
$ export NODE_OPTIONS=""

$ echo $NODE_OPTIONS


$ heroku --version
heroku --version
 ›   Warning: Our terms of service have changed: https://dashboard.heroku.com/terms-of-service
heroku/8.1.9 darwin-x64 node-v16.19.0
```

## Heroku へログイン

```bash
$ heroku login --interactive
heroku: Enter your login credentials
Email [glacier-melt@hotmail.co.jp]:
Password: ******************
 ›   Error: Invalid credentials provided.
 ›
 ›   Error ID: unauthorized

// パスワードを調整して再度ログインする
$ heroku login --interactive
heroku: Enter your login credentials
Email [glacier-melt@hotmail.co.jp]:
Password: ********************
 ›   Error: Your account has MFA enabled; API requests using basic authentication with email and password are not supported. Please generate an authorization token for API access.
 ›
 ›   Error ID: vaas_enrolled

// パスワードに API Key を入力
$ heroku login -i

heroku: Enter your login credentials
Email [glacier-melt@hotmail.co.jp]:
Password: ************************************
Logged in as glacier-melt@hotmail.co.jp
```

## Heroku に本番環境を作成する

```bash
$ heroku create
Creating app... done, ⬢ belle-chocolatine-93694
https://belle-chocolatine-93694-96b147af6341.herokuapp.com/ | https://git.heroku.com/belle-chocolatine-93694.git
$ heroku stack:set heroku-20
Setting stack to heroku-20... done
```

## Heroku にデプロイする

```bash
$ git push heroku main
Enumerating objects: 133, done.
Counting objects: 100% (133/133), done.
Delta compression using up to 10 threads
Compressing objects: 100% (115/115), done.
Writing objects: 100% (133/133), 159.71 KiB | 9.98 MiB/s, done.
Total 133 (delta 23), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (23/23), done.
remote: Updated 90 paths from 268feaf
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> Building on the Heroku-20 stack
remote: -----> Determining which buildpack to use for this app
remote:  !     Warning: Multiple default buildpacks reported the ability to handle this app. The first buildpack in the list below will be used.
remote:                         Detected buildpacks: Ruby,Node.js
remote:                         See https://devcenter.heroku.com/articles/buildpacks#buildpack-detect-order
remote: -----> Ruby app detected
remote: -----> Installing bundler 2.3.25
remote: -----> Removing BUNDLED WITH version in the Gemfile.lock
remote: -----> Compiling Ruby/Rails
remote: -----> Using Ruby version: ruby-2.7.6
remote: -----> Installing dependencies using bundler 2.3.25
remote:        Running: BUNDLE_WITHOUT='development:test' BUNDLE_PATH=vendor/bundle BUNDLE_BIN=vendor/bundle/bin BUNDLE_DEPLOYMENT=1 bundle install -j4
remote:        Your bundle only supports platforms ["x86_64-darwin-21"] but your local platform
remote:        is x86_64-linux. Add the current platform to the lockfile with
remote:        `bundle lock --add-platform x86_64-linux` and try again.
remote:        Bundler Output: Your bundle only supports platforms ["x86_64-darwin-21"] but your local platform
remote:        is x86_64-linux. Add the current platform to the lockfile with
remote:        `bundle lock --add-platform x86_64-linux` and try again.
remote:
remote:  !
remote:  !     Failed to install gems via Bundler.
remote:  !
remote:  !     Push rejected, failed to compile Ruby app.
remote:
remote:  !     Push failed
remote: Verifying deploy...
remote:
remote: !       Push rejected to belle-chocolatine-93694.
remote:
To https://git.heroku.com/belle-chocolatine-93694.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://git.heroku.com/belle-chocolatine-93694.git'

// Gemfile.lock に Linux のプラットフォームを追加する
$ bundle lock --add-platform x86_64-linux
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies...
Writing lockfile to /Volumes/dev/git-dev/rails/hello_app/Gemfile.lock

// 再度デプロイする
git push heroku main
Enumerating objects: 136, done.
Counting objects: 100% (136/136), done.
Delta compression using up to 10 threads
Compressing objects: 100% (118/118), done.
Writing objects: 100% (136/136), 159.96 KiB | 10.00 MiB/s, done.
Total 136 (delta 25), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (25/25), done.
remote: Updated 90 paths from ceec443
remote: Compressing source files... done.
remote: Building source:
remote:
remote: -----> Building on the Heroku-20 stack
remote: -----> Determining which buildpack to use for this app
remote:  !     Warning: Multiple default buildpacks reported the ability to handle this app. The first buildpack in the list below will be used.
remote:                         Detected buildpacks: Ruby,Node.js
remote:                         See https://devcenter.heroku.com/articles/buildpacks#buildpack-detect-order
remote: -----> Ruby app detected
remote: -----> Installing bundler 2.3.25
remote: -----> Removing BUNDLED WITH version in the Gemfile.lock
remote: -----> Compiling Ruby/Rails
remote: -----> Using Ruby version: ruby-2.7.6
remote: -----> Installing dependencies using bundler 2.3.25
remote:        Running: BUNDLE_WITHOUT='development:test' BUNDLE_PATH=vendor/bundle BUNDLE_BIN=vendor/bundle/bin BUNDLE_DEPLOYMENT=1 bundle install -j4
remote:        Fetching gem metadata from https://rubygems.org/..........
remote:        Fetching rake 12.3.3
remote:        Installing rake 12.3.3
remote:        Fetching zeitwerk 2.6.8
remote:        Fetching minitest 5.18.1
remote:        Fetching thread_safe 0.3.6
remote:        Fetching concurrent-ruby 1.2.2
remote:        Installing zeitwerk 2.6.8
remote:        Installing minitest 5.18.1
remote:        Installing concurrent-ruby 1.2.2
remote:        Fetching builder 3.2.4
remote:        Fetching erubi 1.12.0
remote:        Installing thread_safe 0.3.6
remote:        Installing builder 3.2.4
remote:        Installing erubi 1.12.0
remote:        Fetching racc 1.7.1
remote:        Fetching crass 1.0.6
remote:        Fetching rack 2.2.7
remote:        Installing crass 1.0.6
remote:        Installing racc 1.7.1 with native extensions
remote:        Fetching nio4r 2.5.9
remote:        Installing rack 2.2.7
remote:        Fetching websocket-extensions 0.1.5
remote:        Installing nio4r 2.5.9 with native extensions
remote:        Installing websocket-extensions 0.1.5
remote:        Fetching marcel 1.0.2
remote:        Fetching mini_mime 1.1.2
remote:        Installing marcel 1.0.2
remote:        Fetching date 3.3.3
remote:        Installing mini_mime 1.1.2
remote:        Installing date 3.3.3 with native extensions
remote:        Fetching timeout 0.4.0
remote:        Installing timeout 0.4.0
remote:        Fetching msgpack 1.7.1
remote:        Installing msgpack 1.7.1 with native extensions
remote:        Using bundler 2.3.25
remote:        Fetching ffi 1.15.5
remote:        Installing ffi 1.15.5 with native extensions
remote:        Fetching method_source 1.0.0
remote:        Installing method_source 1.0.0
remote:        Fetching pg 1.1.4
remote:        Installing pg 1.1.4 with native extensions
remote:        Fetching thor 1.2.2
remote:        Installing thor 1.2.2
remote:        Fetching rb-fsevent 0.11.2
remote:        Installing rb-fsevent 0.11.2
remote:        Fetching tilt 2.2.0
remote:        Installing tilt 2.2.0
remote:        Fetching turbolinks-source 5.2.0
remote:        Installing turbolinks-source 5.2.0
remote:        Fetching tzinfo 1.2.11
remote:        Installing tzinfo 1.2.11
remote:        Fetching i18n 1.14.1
remote:        Installing i18n 1.14.1
remote:        Fetching websocket-driver 0.7.5
remote:        Installing websocket-driver 0.7.5 with native extensions
remote:        Fetching rack-test 2.1.0
remote:        Installing rack-test 2.1.0
remote:        Fetching rack-proxy 0.7.6
remote:        Installing rack-proxy 0.7.6
remote:        Fetching sprockets 3.7.2
remote:        Installing sprockets 3.7.2
remote:        Fetching net-protocol 0.2.1
remote:        Installing net-protocol 0.2.1
remote:        Fetching nokogiri 1.15.3 (x86_64-linux)
remote:        Installing nokogiri 1.15.3 (x86_64-linux)
remote:        Fetching puma 4.3.6
remote:        Installing puma 4.3.6 with native extensions
remote:        Fetching turbolinks 5.2.0
remote:        Installing turbolinks 5.2.0
remote:        Fetching activesupport 6.0.4
remote:        Installing activesupport 6.0.4
remote:        Fetching bootsnap 1.10.3
remote:        Installing bootsnap 1.10.3 with native extensions
remote:        Fetching net-imap 0.3.6
remote:        Installing net-imap 0.3.6
remote:        Fetching net-pop 0.1.2
remote:        Installing net-pop 0.1.2
remote:        Fetching net-smtp 0.3.3
remote:        Installing net-smtp 0.3.3
remote:        Fetching loofah 2.21.3
remote:        Installing loofah 2.21.3
remote:        Fetching rb-inotify 0.10.1
remote:        Installing rb-inotify 0.10.1
remote:        Fetching rails-dom-testing 2.1.1
remote:        Installing rails-dom-testing 2.1.1
remote:        Fetching globalid 1.1.0
remote:        Installing globalid 1.1.0
remote:        Fetching activemodel 6.0.4
remote:        Fetching jbuilder 2.9.1
remote:        Installing activemodel 6.0.4
remote:        Installing jbuilder 2.9.1
remote:        Fetching mail 2.8.1
remote:        Fetching rails-html-sanitizer 1.6.0
remote:        Installing rails-html-sanitizer 1.6.0
remote:        Installing mail 2.8.1
remote:        Fetching sass-listen 4.0.0
remote:        Installing sass-listen 4.0.0
remote:        Fetching activejob 6.0.4
remote:        Installing activejob 6.0.4
remote:        Fetching activerecord 6.0.4
remote:        Fetching actionview 6.0.4
remote:        Installing actionview 6.0.4
remote:        Installing activerecord 6.0.4
remote:        Fetching sass 3.7.4
remote:        Installing sass 3.7.4
remote:        Fetching actionpack 6.0.4
remote:        Installing actionpack 6.0.4
remote:        Fetching actioncable 6.0.4
remote:        Fetching activestorage 6.0.4
remote:        Installing actioncable 6.0.4
remote:        Installing activestorage 6.0.4
remote:        Fetching actionmailer 6.0.4
remote:        Fetching railties 6.0.4
remote:        Installing actionmailer 6.0.4
remote:        Installing railties 6.0.4
remote:        Fetching sprockets-rails 3.4.2
remote:        Installing sprockets-rails 3.4.2
remote:        Fetching actionmailbox 6.0.4
remote:        Installing actionmailbox 6.0.4
remote:        Fetching actiontext 6.0.4
remote:        Installing actiontext 6.0.4
remote:        Fetching rails 6.0.4
remote:        Fetching sass-rails 5.1.0
remote:        Installing sass-rails 5.1.0
remote:        Installing rails 6.0.4
remote:        Fetching webpacker 4.0.7
remote:        Installing webpacker 4.0.7
remote:        Bundle complete! 18 Gemfile dependencies, 64 gems now installed.
remote:        Gems in the groups 'development' and 'test' were not installed.
remote:        Bundled gems are installed into `./vendor/bundle`
remote:        Post-install message from sass:
remote:
remote:        Ruby Sass has reached end-of-life and should no longer be used.
remote:
remote:        * If you use Sass as a command-line tool, we recommend using Dart Sass, the new
remote:          primary implementation: https://sass-lang.com/install
remote:
remote:        * If you use Sass as a plug-in for a Ruby web framework, we recommend using the
remote:          sassc gem: https://github.com/sass/sassc-ruby#readme
remote:
remote:        * For more details, please refer to the Sass blog:
remote:          https://sass-lang.com/blog/posts/7828841
remote:
remote:        Bundle completed (28.42s)
remote:        Cleaning up the bundler cache.
remote: -----> Installing node-v16.18.1-linux-x64
remote: -----> Installing yarn-v1.22.19
remote: -----> Detecting rake tasks
remote: -----> Preparing app for Rails asset pipeline
remote:        Running: rake assets:precompile
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
remote:        yarn install v1.22.19
remote:        [1/4] Resolving packages...
remote:        [2/4] Fetching packages...
remote:        [3/4] Linking dependencies...
remote:        warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
remote:        [4/4] Building fresh packages...
remote:        Done in 13.25s.
remote:        I, [2023-07-14T16:29:38.517562 #1080]  INFO -- : Writing /tmp/build_b712f0ae/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css
remote:        I, [2023-07-14T16:29:38.517891 #1080]  INFO -- : Writing /tmp/build_b712f0ae/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css.gz
remote:        Compiling
remote:        Compiled all packs in /tmp/build_b712f0ae/public/packs
remote:        Though the "loose" option was set to "false" in your @babel/preset-env config, it will not be used for @babel/plugin-transform-private-property-in-object since the "loose" mode option was set to "true" for @babel/plugin-transform-class-properties.
remote:        The "loose" option must be the same for @babel/plugin-transform-class-properties, @babel/plugin-transform-private-methods and @babel/plugin-transform-private-property-in-object (when they are enabled): you can silence this warning by explicitly adding
remote:         ["@babel/plugin-transform-private-property-in-object", { "loose": true }]
remote:        to the "plugins" section of your Babel config.
remote:        Though the "loose" option was set to "false" in your @babel/preset-env config, it will not be used for @babel/plugin-transform-private-methods since the "loose" mode option was set to "true" for @babel/plugin-transform-private-property-in-object.
remote:        The "loose" option must be the same for @babel/plugin-transform-class-properties, @babel/plugin-transform-private-methods and @babel/plugin-transform-private-property-in-object (when they are enabled): you can silence this warning by explicitly adding
remote:         ["@babel/plugin-transform-private-methods", { "loose": true }]
remote:        to the "plugins" section of your Babel config.
remote:        Though the "loose" option was set to "false" in your @babel/preset-env config, it will not be used for @babel/plugin-transform-private-property-in-object since the "loose" mode option was set to "true" for @babel/plugin-transform-class-properties.
remote:        The "loose" option must be the same for @babel/plugin-transform-class-properties, @babel/plugin-transform-private-methods and @babel/plugin-transform-private-property-in-object (when they are enabled): you can silence this warning by explicitly adding
remote:         ["@babel/plugin-transform-private-property-in-object", { "loose": true }]
remote:        to the "plugins" section of your Babel config.
remote:        Though the "loose" option was set to "false" in your @babel/preset-env config, it will not be used for @babel/plugin-transform-private-methods since the "loose" mode option was set to "true" for @babel/plugin-transform-private-property-in-object.
remote:        The "loose" option must be the same for @babel/plugin-transform-class-properties, @babel/plugin-transform-private-methods and @babel/plugin-transform-private-property-in-object (when they are enabled): you can silence this warning by explicitly adding
remote:         ["@babel/plugin-transform-private-methods", { "loose": true }]
remote:        to the "plugins" section of your Babel config.
remote:
remote:        Asset precompilation completed (20.10s)
remote:        Cleaning assets
remote:        Running: rake assets:clean
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
remote:        /tmp/build_b712f0ae/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
remote:        /tmp/build_b712f0ae/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
remote: -----> Detecting rails configuration
remote:
remote: ###### WARNING:
remote:
remote:        Detecting rails configuration failed
remote:        set HEROKU_DEBUG_RAILS_RUNNER=1 to debug
remote:
remote: ###### WARNING:
remote:
remote:        There is a more recent Ruby version available for you to use:
remote:
remote:        2.7.8
remote:
remote:        The latest version will include security and bug fixes. We always recommend
remote:        running the latest version of your minor release.
remote:
remote:        Please upgrade your Ruby version.
remote:
remote:        For all available Ruby versions see:
remote:          https://devcenter.heroku.com/articles/ruby-support#supported-runtimes
remote:
remote: ###### WARNING:
remote:
remote:        Potential EOL Ruby Version
remote:
remote:        You are using a Ruby version that has either reached its End of Life (EOL)
remote:        or will reach its End of Life on December 25th of this year.
remote:
remote:        We suggest you upgrade to Ruby 3.0.x or later
remote:
remote:        Once a Ruby version becomes EOL, it will no longer receive
remote:        security updates from Ruby core and may have serious vulnerabilities.
remote:
remote:        Please upgrade your Ruby version.
remote:
remote:        For a list of supported Ruby versions see:
remote:          https://devcenter.heroku.com/articles/ruby-support#supported-runtimes
remote:
remote: ###### WARNING:
remote:
remote:        No Procfile detected, using the default web server.
remote:        We recommend explicitly declaring how to boot your server process via a Procfile.
remote:        https://devcenter.heroku.com/articles/ruby-default-web-server
remote:
remote:
remote: -----> Discovering process types
remote:        Procfile declares types     -> (none)
remote:        Default types for buildpack -> console, rake, web
remote:
remote: -----> Compressing...
remote:        Done: 79M
remote: -----> Launching...
remote:  !     The following add-ons were automatically provisioned: heroku-postgresql. These add-ons may incur additional cost, which is prorated to the second. Run `heroku addons` for more info.
remote:        Released v7
remote:        https://belle-chocolatine-93694-96b147af6341.herokuapp.com/ deployed to Heroku
remote:
remote: This app is using the Heroku-20 stack, however a newer stack is available.
remote: To upgrade to Heroku-22, see:
remote: https://devcenter.heroku.com/articles/upgrading-to-the-latest-stack
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/belle-chocolatine-93694.git
 * [new branch]      main -> main
```

## アプリケーションの名前を変更する

```bash
$ heroku rename rails-tutorial-hello-glaciermelt
Renaming belle-chocolatine-93694 to rails-tutorial-hello-glaciermelt... !
 ▸    Name is too long (maximum is 30 characters)
```

## Heroku コマンド

```bash
$ heroku help
CLI to interact with Heroku

VERSION
  heroku/8.1.9 darwin-x64 node-v16.19.0

USAGE
  $ heroku [COMMAND]

TOPICS
  access          manage user access to apps
  addons          tools and services for developing, extending, and operating your app
  apps            manage apps on Heroku
  auth            check 2fa status
  authorizations  OAuth authorizations
  buildpacks      scripts used to compile apps
  certs           a topic for the ssl plugin
  ci              run an application test suite on Heroku
  clients         OAuth clients on the platform
  config          environment variables of apps
  container       Use containers to build and deploy Heroku apps
  domains         custom domains for apps
  drains          forward logs to syslog or HTTPS
  features        add/remove app features
  git             manage local git repository for app
  keys            add/remove account ssh keys
  labs            add/remove experimental features
  local           run Heroku app locally
  maintenance     enable/disable access to app
  members         manage organization members
  orgs            manage organizations
  pg              manage postgresql databases
  pipelines       manage pipelines
  plugins         List installed plugins.
  ps              Client tools for Heroku Exec
  redis           manage heroku redis instances
  releases        display the releases for an app
  reviewapps      manage reviewapps in pipelines
  run             run a one-off process inside a Heroku dyno
  sessions        OAuth sessions
  spaces          manage heroku private spaces
  webhooks        list webhooks on an app

COMMANDS
  2fa             check 2fa status
  access          list who has access to an app
  addons          lists your add-ons and attachments
  apps            list your apps
  authorizations  list OAuth authorizations
  autocomplete    display autocomplete installation instructions
  buildpacks      display the buildpacks for an app
  certs           list SSL certificates for an app
  ci              display the most recent CI runs for the given pipeline
  clients         list your OAuth clients
  commands        list all the commands
  config          display the config vars for an app
  container       Use containers to build and deploy Heroku apps
  domains         list domains for an app
  drains          display the log drains of an app
  features        list available app features
  help            Display help for heroku.
  join            add yourself to a team app
  keys            display your SSH keys
  labs            list experimental features
  leave           remove yourself from a team app
  local           run heroku app locally
  lock            prevent team members from joining an app
  login           login with your Heroku credentials
  logout          clears local login credentials and invalidates API session
  logs            display recent log output
  maintenance     display the current maintenance status of app
  members         list members of a team
  notifications   display notifications
  orgs            list the teams that you are a member of
  pg              show database information
  pipelines       list pipelines you have access to
  plugins         List installed plugins.
  ps              list dynos for an app
  psql            open a psql shell to the database
  redis           gets information about redis
  regions         list available regions for deployment
  releases        display the releases for an app
  run             run a one-off process inside a heroku dyno
  sessions        list your OAuth sessions
  spaces          list available spaces
  status          display current status of the Heroku platform
  teams           list the teams that you are a member of
  trusted-ips     list trusted IP ranges for a space
  twofactor       check 2fa status
  unlock          unlock an app so any team member can join
  update          update the heroku CLI
  version
  webhooks        list webhooks on an app
  which           Show which plugin a command is in.
  whoami          display the current logged in user

$ heroku logs
2023-07-14T16:19:43.178076+00:00 app[api]: Initial release by user glacier-melt@hotmail.co.jp
2023-07-14T16:19:43.178076+00:00 app[api]: Release v1 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:19:43.339669+00:00 app[api]: Release v2 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:19:43.339669+00:00 app[api]: Enable Logplex by user glacier-melt@hotmail.co.jp
2023-07-14T16:21:24.886083+00:00 app[api]: Stack changed from heroku-22 to heroku-20 by user glacier-melt@hotmail.co.jp
2023-07-14T16:21:24.898163+00:00 app[api]: Upgrade stack to heroku-20 by user glacier-melt@hotmail.co.jp
2023-07-14T16:21:24.898163+00:00 app[api]: Release v3 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:23:40.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-14T16:23:43.000000+00:00 app[api]: Build failed -- check your build output: https://dashboard.heroku.com/apps/85ff57a3-3ac1-4bea-b9af-39de1c96f208/activity/builds/16091d3a-a1c8-4a8c-b11a-1162fb1814da
2023-07-14T16:25:15.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-14T16:25:18.000000+00:00 app[api]: Build failed -- check your build output: https://dashboard.heroku.com/apps/85ff57a3-3ac1-4bea-b9af-39de1c96f208/activity/builds/aad43f29-9244-49a3-bee9-d6ce128faec1
2023-07-14T16:28:49.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.050665+00:00 app[api]: Set LANG, RACK_ENV, RAILS_ENV, RAILS_LOG_TO_STDOUT, RAILS_SERVE_STATIC_FILES, SECRET_KEY_BASE config vars by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.050665+00:00 app[api]: Release v4 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.767992+00:00 app[api]: Attach DATABASE (@ref:postgresql-flat-02648) by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.767992+00:00 app[api]: Running release v5 commands by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.779029+00:00 app[api]: @ref:postgresql-flat-02648 completed provisioning, setting DATABASE_URL. by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:53.779029+00:00 app[api]: Release v6 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:54.138551+00:00 app[api]: Deploy 954ab531 by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:54.138551+00:00 app[api]: Release v7 created by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:54.154852+00:00 app[api]: Scaled to console@0:Basic rake@0:Basic web@1:Basic by user glacier-melt@hotmail.co.jp
2023-07-14T16:29:57.000000+00:00 app[api]: Build succeeded
2023-07-14T16:29:58.521866+00:00 heroku[web.1]: Starting process with command `bin/rails server -p ${PORT:-5000} -e production`
2023-07-14T16:30:00.738962+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
2023-07-14T16:30:00.739007+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
2023-07-14T16:30:00.739009+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
2023-07-14T16:30:00.739009+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
2023-07-14T16:30:00.739009+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
2023-07-14T16:30:00.739010+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
2023-07-14T16:30:00.785959+00:00 app[web.1]: => Booting Puma
2023-07-14T16:30:00.785960+00:00 app[web.1]: => Rails 6.0.4 application starting in production
2023-07-14T16:30:00.785960+00:00 app[web.1]: => Run `rails server --help` for more startup options
2023-07-14T16:30:01.480531+00:00 app[web.1]: Puma starting in single mode...
2023-07-14T16:30:01.480557+00:00 app[web.1]: * Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
2023-07-14T16:30:01.480558+00:00 app[web.1]: * Min threads: 5, max threads: 5
2023-07-14T16:30:01.480559+00:00 app[web.1]: * Environment: production
2023-07-14T16:30:01.480709+00:00 app[web.1]: * Listening on tcp://0.0.0.0:4892
2023-07-14T16:30:01.480870+00:00 app[web.1]: Use Ctrl-C to stop
2023-07-14T16:30:02.002085+00:00 heroku[web.1]: State changed from starting to up
2023-07-14T16:31:29.139143+00:00 app[web.1]: I, [2023-07-14T16:31:29.139071 #2]  INFO -- : [e1765b5f-43c5-450d-9e23-ef703bec0fe0] Started GET "/" for 217.178.26.43 at 2023-07-14 16:31:29 +0000
2023-07-14T16:31:29.140462+00:00 app[web.1]: I, [2023-07-14T16:31:29.140418 #2]  INFO -- : [e1765b5f-43c5-450d-9e23-ef703bec0fe0] Processing by ApplicationController#goodbye as HTML
2023-07-14T16:31:29.143121+00:00 app[web.1]: I, [2023-07-14T16:31:29.143084 #2]  INFO -- : [e1765b5f-43c5-450d-9e23-ef703bec0fe0]   Rendering html template
2023-07-14T16:31:29.143211+00:00 app[web.1]: I, [2023-07-14T16:31:29.143191 #2]  INFO -- : [e1765b5f-43c5-450d-9e23-ef703bec0fe0]   Rendered html template (Duration: 0.0ms | Allocations: 5)
2023-07-14T16:31:29.143351+00:00 app[web.1]: I, [2023-07-14T16:31:29.143331 #2]  INFO -- : [e1765b5f-43c5-450d-9e23-ef703bec0fe0] Completed 200 OK in 3ms (Views: 0.5ms | Allocations: 540)
2023-07-14T16:31:29.144306+00:00 heroku[router]: at=info method=GET path="/" host=belle-chocolatine-93694-96b147af6341.herokuapp.com request_id=e1765b5f-43c5-450d-9e23-ef703bec0fe0 fwd="217.178.26.43" dyno=web.1 connect=0ms service=11ms status=200 bytes=514 protocol=https
2023-07-14T16:31:29.430084+00:00 heroku[router]: at=info method=GET path="/favicon.ico" host=belle-chocolatine-93694-96b147af6341.herokuapp.com request_id=50c88f48-60b0-41df-ae16-ad6a8544ade0 fwd="217.178.26.43" dyno=web.1 connect=0ms service=4ms status=200 bytes=143 protocol=https
```
