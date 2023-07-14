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
