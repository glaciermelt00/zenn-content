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
.
.
.
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
.
.
.
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
.
.
.
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
.
.
.
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
