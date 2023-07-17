---
title: "Rails の学び直し: 5th Toy アプリケーション: 2nd"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# Toy アプリケーション: 2nd

## Users リソース

```bash
$ rails generate scaffold User name:string email:string
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
Running via Spring preloader in process 99723
      invoke  active_record
      create    db/migrate/20230716103741_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
      invoke  resource_route
       route    resources :users
      invoke  scaffold_controller
      create    app/controllers/users_controller.rb
      invoke    erb
      create      app/views/users
      create      app/views/users/index.html.erb
      create      app/views/users/edit.html.erb
      create      app/views/users/show.html.erb
      create      app/views/users/new.html.erb
      create      app/views/users/_form.html.erb
      invoke    test_unit
      create      test/controllers/users_controller_test.rb
      create      test/system/users_test.rb
      invoke    helper
      create      app/helpers/users_helper.rb
      invoke      test_unit
      invoke    jbuilder
      create      app/views/users/index.json.jbuilder
      create      app/views/users/show.json.jbuilder
      create      app/views/users/_user.json.jbuilder
      invoke  assets
      invoke    scss
      create      app/assets/stylesheets/users.scss
      invoke  scss
      create    app/assets/stylesheets/scaffolds.scss
```

## データベースをマイグレートする

```bash
$ rails db:migrate
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
== 20230716103741 CreateUsers: migrating ======================================
-- create_table(:users)
   -> 0.0013s
== 20230716103741 CreateUsers: migrated (0.0013s) =============================

glaciermelt (i386):/Volumes/de
```

### 警告を回避する

https://zenn.dev/tarou_yuruyuru/articles/163f5b734409f7

```ruby
# Gemfile

gem 'net-http'
```

```bash
$ bundle install
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies...
Using rake 12.3.3
Using concurrent-ruby 1.2.2
Using erubi 1.12.0
Using racc 1.7.1
Using crass 1.0.6
Using rack 2.2.7
Using date 3.3.3
Using public_suffix 5.0.3
Using bindex 0.8.1
Using msgpack 1.7.1
Using bundler 2.2.17
Using byebug 11.0.1
Using regexp_parser 1.8.2
Using childprocess 2.0.0
Using mini_mime 1.1.2
Using rb-fsevent 0.11.2
Using ruby_dep 1.5.0
Using method_source 1.0.0
Using minitest 5.18.1
Using thor 1.2.2
Using zeitwerk 2.6.8
Using rubyzip 1.3.0
Using spring 2.1.0
Using sqlite3 1.4.2
Using turbolinks-source 5.2.0
Using websocket-extensions 0.1.5
Using nio4r 2.5.9
Using rack-test 2.1.0
Using rack-proxy 0.7.6
Using builder 3.2.4
Using addressable 2.8.4
Fetching uri 0.12.2
Using timeout 0.4.0
Using bootsnap 1.10.3
Using selenium-webdriver 3.142.4
Using websocket-driver 0.7.5
Using puma 4.3.6
Using turbolinks 5.2.0
Using sprockets 3.7.2
Using tilt 2.2.0
Using ffi 1.15.5
Using net-protocol 0.2.1
Using marcel 1.0.2
Using nokogiri 1.15.3 (x86_64-darwin)
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using rb-inotify 0.10.1
Using i18n 1.14.1
Using loofah 2.21.3
Using xpath 3.2.0
Using listen 3.1.5
Using sass-listen 4.0.0
Using webdrivers 4.1.2
Using net-imap 0.3.6
Using thread_safe 0.3.6
Using rails-html-sanitizer 1.6.0
Using tzinfo 1.2.11
Using capybara 3.28.0
Using activesupport 6.0.4
Using spring-watcher-listen 2.0.1
Using mail 2.8.1
Using sass 3.7.4
Using rails-dom-testing 2.1.1
Using globalid 1.1.0
Using activemodel 6.0.4
Using activejob 6.0.4
Using jbuilder 2.9.1
Using actionview 6.0.4
Using activerecord 6.0.4
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
Installing uri 0.12.2
Fetching net-http 0.3.2
Installing net-http 0.3.2
Bundle complete! 19 Gemfile dependencies, 82 gems now installed.
Gems in the group 'production' were not installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```

## Micropots リソース

```bash
$ rails generate scaffold Micropost content:text user_id:integer
Running via Spring preloader in process 91138
      invoke  active_record
      create    db/migrate/20230717013928_create_microposts.rb
      create    app/models/micropost.rb
      invoke    test_unit
      create      test/models/micropost_test.rb
      create      test/fixtures/microposts.yml
      invoke  resource_route
       route    resources :microposts
      invoke  scaffold_controller
      create    app/controllers/microposts_controller.rb
      invoke    erb
      create      app/views/microposts
      create      app/views/microposts/index.html.erb
      create      app/views/microposts/edit.html.erb
      create      app/views/microposts/show.html.erb
      create      app/views/microposts/new.html.erb
      create      app/views/microposts/_form.html.erb
      invoke    test_unit
      create      test/controllers/microposts_controller_test.rb
      create      test/system/microposts_test.rb
      invoke    helper
      create      app/helpers/microposts_helper.rb
      invoke      test_unit
      invoke    jbuilder
      create      app/views/microposts/index.json.jbuilder
      create      app/views/microposts/show.json.jbuilder
      create      app/views/microposts/_micropost.json.jbuilder
      invoke  assets
      invoke    scss
      create      app/assets/stylesheets/microposts.scss
      invoke  scss
   identical    app/assets/stylesheets/scaffolds.scss
```

## データベースをマイグレートする

```bash
$ rails db:migrate
== 20230717013928 CreateMicroposts: migrating =================================
-- create_table(:microposts)
   -> 0.0017s
== 20230717013928 CreateMicroposts: migrated (0.0017s) ========================

```

## バリデーションの導入

```ruby
# app/models/micropost.rb

class Micropost < ApplicationRecord
  validates :content, length: { maximum: 140 }
end
```

## User と Micropost の関連付け

1人のユーザーに、複数のマイクロポストがある。

```ruby
# app/models/user.rb

class User < ApplicationRecord
  has_many :microposts
end
```

1つのマイクロポストは、1人のユーザーに属する。

```ruby
# app/models/micropost.rb

class Micropost < ApplicationRecord
  belongs_to :user
  validates :content, length: { maximum: 140 }
end
```

## Rails コンソールで、アプリケーションの状態を調べる

```bash
$ rails console
Running via Spring preloader in process 18499
Loading development environment (Rails 6.0.4)
2.7.6 :001 > first_user = User.first
   (0.5ms)  SELECT sqlite_version(*)
  User Load (0.1ms)  SELECT "users".* FROM "users" ORDER BY "users"."id" ASC LIMIT ?  [["LIMIT", 1]]
 => #<User id: 1, name: "g1Edited", email: "g1@x.x", created_at: "2023-07-17 00:37:05", updated_at: "2023-07-17 00:37:28">
2.7.6 :002 > first_user.microposts
  Micropost Load (0.1ms)  SELECT "microposts".* FROM "microposts" WHERE "microposts"."user_id" = ? LIMIT ?  [["user_id", 1], ["LIMIT", 11]]
 => #<ActiveRecord::Associations::CollectionProxy [#<Micropost id: 3, content: "microposts1", user_id: 1, created_at: "2023-07-17 02:01:07", updated_at: "2023-07-17 02:01:07">]>
2.7.6 :003 > micropost = first_user.microposts.first
  Micropost Load (0.2ms)  SELECT "microposts".* FROM "microposts" WHERE "microposts"."user_id" = ? ORDER BY "microposts"."id" ASC LIMIT ?  [["user_id", 1], ["LIMIT", 1]]
 => #<Micropost id: 3, content: "microposts1", user_id: 1, created_at: "2023-07-17 02:01:07", updated_at: "2023-07-17 02:01:07">
2.7.6 :004 > micropost.user
 => #<User id: 1, name: "g1Edited", email: "g1@x.x", created_at: "2023-07-17 00:37:05", updated_at: "2023-07-17 00:37:28">
2.7.6 :005 >
```

##
