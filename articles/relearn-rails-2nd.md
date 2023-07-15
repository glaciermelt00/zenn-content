---
title: "Rails の学び直し: 2nd"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# hello_app の作成

## rails コマンドで　hello_app を作る

```bash
$ mkdir rails
$ cd rails 
$ rails _6.0.4_ new hello_app
rails _6.0.4_ new hello_app
      create
      create  README.md
      create  Rakefile
      create  .ruby-version
      create  config.ru
      create  .gitignore
      create  Gemfile
         run  git init from "."
Initialized empty Git repository in /Volumes/dev/git-dev/rails/hello_app/.git/
      create  package.json
      create  app
      create  app/assets/config/manifest.js
      create  app/assets/stylesheets/application.css
      create  app/channels/application_cable/channel.rb
      create  app/channels/application_cable/connection.rb
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/javascript/channels/consumer.js
      create  app/javascript/channels/index.js
      create  app/javascript/packs/application.js
      create  app/jobs/application_job.rb
      create  app/mailers/application_mailer.rb
      create  app/models/application_record.rb
      create  app/views/layouts/application.html.erb
      create  app/views/layouts/mailer.html.erb
      create  app/views/layouts/mailer.text.erb
      create  app/assets/images
      create  app/assets/images/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      create  bin
      create  bin/rails
      create  bin/rake
      create  bin/setup
      create  bin/yarn
      create  config
      create  config/routes.rb
      create  config/application.rb
      create  config/environment.rb
      create  config/cable.yml
      create  config/puma.rb
      create  config/spring.rb
      create  config/storage.yml
      create  config/environments
      create  config/environments/development.rb
      create  config/environments/production.rb
      create  config/environments/test.rb
      create  config/initializers
      create  config/initializers/application_controller_renderer.rb
      create  config/initializers/assets.rb
      create  config/initializers/backtrace_silencers.rb
      create  config/initializers/content_security_policy.rb
      create  config/initializers/cookies_serializer.rb
      create  config/initializers/cors.rb
      create  config/initializers/filter_parameter_logging.rb
      create  config/initializers/inflections.rb
      create  config/initializers/mime_types.rb
      create  config/initializers/new_framework_defaults_6_0.rb
      create  config/initializers/wrap_parameters.rb
      create  config/locales
      create  config/locales/en.yml
      create  config/master.key
      append  .gitignore
      create  config/boot.rb
      create  config/database.yml
      create  db
      create  db/seeds.rb
      create  lib
      create  lib/tasks
      create  lib/tasks/.keep
      create  lib/assets
      create  lib/assets/.keep
      create  log
      create  log/.keep
      create  public
      create  public/404.html
      create  public/422.html
      create  public/500.html
      create  public/apple-touch-icon-precomposed.png
      create  public/apple-touch-icon.png
      create  public/favicon.ico
      create  public/robots.txt
      create  tmp
      create  tmp/.keep
      create  tmp/pids
      create  tmp/pids/.keep
      create  tmp/cache
      create  tmp/cache/assets
      create  vendor
      create  vendor/.keep
      create  test/fixtures
      create  test/fixtures/.keep
      create  test/fixtures/files
      create  test/fixtures/files/.keep
      create  test/controllers
      create  test/controllers/.keep
      create  test/mailers
      create  test/mailers/.keep
      create  test/models
      create  test/models/.keep
      create  test/helpers
      create  test/helpers/.keep
      create  test/integration
      create  test/integration/.keep
      create  test/channels/application_cable/connection_test.rb
      create  test/test_helper.rb
      create  test/system
      create  test/system/.keep
      create  test/application_system_test_case.rb
      create  storage
      create  storage/.keep
      create  tmp/storage
      create  tmp/storage/.keep
      remove  config/initializers/cors.rb
      remove  config/initializers/new_framework_defaults_6_0.rb
         run  bundle install
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies.....
Fetching rake 13.0.6
Installing rake 13.0.6
Using concurrent-ruby 1.2.2
Using websocket-extensions 0.1.5
Using marcel 1.0.2
Using mini_mime 1.1.2
Fetching minitest 5.18.1
Fetching racc 1.7.1
Using rack 2.2.7
Using nio4r 2.5.9
Using thread_safe 0.3.6
Fetching timeout 0.4.0
Fetching bindex 0.8.1
Using erubi 1.12.0
Using crass 1.0.6
Using bundler 2.2.17
Fetching date 3.3.3
Using zeitwerk 2.6.8
Fetching matrix 0.4.2
Fetching public_suffix 5.0.3
Using builder 3.2.4
Fetching regexp_parser 2.8.1
Fetching msgpack 1.7.1
Fetching byebug 11.1.3
Installing racc 1.7.1 with native extensions
Installing timeout 0.4.0
Installing bindex 0.8.1 with native extensions
Installing matrix 0.4.2
Installing msgpack 1.7.1 with native extensions
Installing regexp_parser 2.8.1
Installing date 3.3.3 with native extensions
Installing byebug 11.1.3 with native extensions
Installing minitest 5.18.1
Installing public_suffix 5.0.3
Using method_source 1.0.0
Using thor 1.2.2
Fetching ffi 1.15.5
Fetching rb-fsevent 0.11.2
Installing rb-fsevent 0.11.2
Installing ffi 1.15.5 with native extensions
Fetching rexml 3.2.5
Fetching rubyzip 2.3.2
Fetching tilt 2.2.0
Using i18n 1.14.1
Using websocket-driver 0.7.5
Using rack-test 2.1.0
Installing tilt 2.2.0
Installing rubyzip 2.3.2
Installing rexml 3.2.5
Using sprockets 4.2.0
Using tzinfo 1.2.11
Using net-protocol 0.2.1
Using nokogiri 1.15.3 (x86_64-darwin)
Fetching websocket 1.2.9
Fetching spring 2.1.1
Fetching turbolinks-source 5.2.0
Fetching sqlite3 1.6.3 (x86_64-darwin)
Installing websocket 1.2.9
Installing turbolinks-source 5.2.0
Installing spring 2.1.1
Using net-imap 0.3.6
Using loofah 2.21.3
Installing sqlite3 1.6.3 (x86_64-darwin)
Fetching puma 4.3.12
Fetching rack-proxy 0.7.6
Fetching addressable 2.8.4
Fetching bootsnap 1.16.0
Fetching net-smtp 0.3.3
Fetching activesupport 6.0.6.1
Fetching net-pop 0.1.2
Fetching xpath 3.2.0
Fetching turbolinks 5.2.1
Fetching selenium-webdriver 4.9.0
Installing rack-proxy 0.7.6
Installing bootsnap 1.16.0 with native extensions
Installing net-smtp 0.3.3
Installing net-pop 0.1.2
Installing turbolinks 5.2.1
Installing xpath 3.2.0
Installing puma 4.3.12 with native extensions
Installing addressable 2.8.4
Using rails-html-sanitizer 1.6.0
Using mail 2.8.1
Installing activesupport 6.0.6.1
Using rails-dom-testing 2.1.1
Using globalid 1.1.0
Fetching capybara 3.39.2
Fetching sassc 2.4.0
Fetching rb-inotify 0.10.1
Installing rb-inotify 0.10.1
Installing sassc 2.4.0 with native extensions
Installing selenium-webdriver 4.9.0
Installing capybara 3.39.2
Fetching activemodel 6.0.6.1
Fetching actionview 6.0.6.1
Fetching listen 3.8.0
Fetching activejob 6.0.6.1
Installing activejob 6.0.6.1
Installing activemodel 6.0.6.1
Installing listen 3.8.0
Installing actionview 6.0.6.1
Fetching spring-watcher-listen 2.0.1
Fetching webdrivers 5.2.0
Fetching activerecord 6.0.6.1
Fetching actionpack 6.0.6.1
Fetching jbuilder 2.11.5
Installing webdrivers 5.2.0
Installing spring-watcher-listen 2.0.1
Installing jbuilder 2.11.5
Installing actionpack 6.0.6.1
Installing activerecord 6.0.6.1
Using sprockets-rails 3.4.2
Fetching actioncable 6.0.6.1
Fetching actionmailer 6.0.6.1
Fetching railties 6.0.6.1
Installing actionmailer 6.0.6.1
Installing actioncable 6.0.6.1
Installing railties 6.0.6.1
Fetching activestorage 6.0.6.1
Installing activestorage 6.0.6.1
Fetching actionmailbox 6.0.6.1
Fetching actiontext 6.0.6.1
Installing actiontext 6.0.6.1
Installing actionmailbox 6.0.6.1
Fetching sassc-rails 2.1.2
Fetching web-console 4.2.0
Fetching webpacker 4.3.0
Fetching rails 6.0.6.1
Installing sassc-rails 2.1.2
Installing web-console 4.2.0
Installing webpacker 4.3.0
Installing rails 6.0.6.1
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    current directory: /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/puma-4.3.12/ext/puma_http11
/Users/glaciermelt/.rvm/rubies/ruby-2.7.6/bin/ruby -I /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0 -r ./siteconf20230714-35298-nuyb7h.rb extconf.rb
checking for BIO_read() in -lcrypto... yes
checking for SSL_CTX_new() in -lssl... yes
checking for openssl/bio.h... yes
checking for DTLS_method() in openssl/ssl.h... yes
checking for TLS_server_method() in openssl/ssl.h... yes
checking for SSL_CTX_set_min_proto_version in openssl/ssl.h... no
checking for Random.bytes... yes
creating Makefile

current directory: /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/puma-4.3.12/ext/puma_http11
make "DESTDIR=" clean

current directory: /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/puma-4.3.12/ext/puma_http11
make "DESTDIR="
compiling http11_parser.c
compiling io_buffer.c
compiling mini_ssl.c
mini_ssl.c:196:21: error: implicit declaration of function 'TLS_server_method' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
  ctx = SSL_CTX_new(TLS_server_method());
                    ^
mini_ssl.c:196:21: note: did you mean 'TLSv1_server_method'?
/Users/glaciermelt/.rvm/usr/include/openssl/ssl.h:1883:19: note: 'TLSv1_server_method' declared here
const SSL_METHOD *TLSv1_server_method(void);    /* TLSv1.0 */
                  ^
mini_ssl.c:196:21: warning: incompatible integer to pointer conversion passing 'int' to parameter of type 'const SSL_METHOD *' (aka 'const struct ssl_method_st *') [-Wint-conversion]
  ctx = SSL_CTX_new(TLS_server_method());
                    ^~~~~~~~~~~~~~~~~~~
/Users/glaciermelt/.rvm/usr/include/openssl/ssl.h:1676:40: note: passing argument to parameter 'meth' here
SSL_CTX *SSL_CTX_new(const SSL_METHOD *meth);
                                       ^
mini_ssl.c:301:27: error: implicit declaration of function 'DTLS_method' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
  conn->ctx = SSL_CTX_new(DTLS_method());
                          ^
mini_ssl.c:301:27: note: did you mean 'DTLSv1_method'?
/Users/glaciermelt/.rvm/usr/include/openssl/ssl.h:1895:19: note: 'DTLSv1_method' declared here
const SSL_METHOD *DTLSv1_method(void);          /* DTLSv1.0 */
                  ^
mini_ssl.c:301:27: warning: incompatible integer to pointer conversion passing 'int' to parameter of type 'const SSL_METHOD *' (aka 'const struct ssl_method_st *') [-Wint-conversion]
  conn->ctx = SSL_CTX_new(DTLS_method());
                          ^~~~~~~~~~~~~
/Users/glaciermelt/.rvm/usr/include/openssl/ssl.h:1676:40: note: passing argument to parameter 'meth' here
SSL_CTX *SSL_CTX_new(const SSL_METHOD *meth);
                                       ^
2 warnings and 2 errors generated.
make: *** [mini_ssl.o] Error 1

make failed, exit code 2

Gem files will remain installed in /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/puma-4.3.12 for inspection.
Results logged to /Users/glaciermelt/.rvm/gems/ruby-2.7.6/extensions/x86_64-darwin-21/2.7.0/puma-4.3.12/gem_make.out

An error occurred while installing puma (4.3.12), and Bundler cannot continue.
Make sure that `gem install puma -v '4.3.12' --source 'https://rubygems.org/'` succeeds before bundling.

In Gemfile:
  puma
         run  bundle binstubs bundler
Could not find gem 'puma (~> 4.1)' in rubygems repository https://rubygems.org/ or installed locally.
The source does not contain any versions of 'puma'
         run  bundle exec spring binstub --all
Could not find gem 'puma (~> 4.1)' in rubygems repository https://rubygems.org/ or installed locally.
The source does not contain any versions of 'puma'
Run `bundle install` to install missing gems.
       rails  webpacker:install
Could not find gem 'puma (~> 4.1)' in rubygems repository https://rubygems.org/ or installed locally.
The source does not contain any versions of 'puma'
Run `bundle install` to install missing gems.
```

### bundle install する


```bash
// OpenSSL のバージョンを確認
$ openssl version

OpenSSL 3.1.1 30 May 2023 (Library: OpenSSL 3.1.1 30 May 2023)

// brew で openssl の情報を確認
$ brew info openssl
==> openssl@3: stable 3.1.1 (bottled)
Cryptography and SSL/TLS Toolkit
https://openssl.org/
/usr/local/Cellar/openssl@3/3.1.1_1 (6,495 files, 30.0MB) *
  Poured from bottle on 2023-07-01 at 13:44:37
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/openssl@3.rb
License: Apache-2.0
==> Dependencies
Required: ca-certificates ✔
==> Caveats
A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
  /usr/local/etc/openssl@3/certs

and run
  /usr/local/opt/openssl@3/bin/c_rehash
==> Analytics
install: 7,403 (30 days), 7,403 (90 days), 7,403 (365 days)
install-on-request: 597 (30 days), 597 (90 days), 597 (365 days)
build-error: 108 (30 days)

// openssl のディレクトリを確認
$ ls /usr/local/Cellar/openssl@3/3.1.1_1
bin  include  lib  share  AUTHORS.md  CHANGES.md  INSTALL_RECEIPT.json  LICENSE.txt  NEWS.md  README.md

// bundle config を設定
$ bundle config --local build.puma --with-opt-dir=/usr/local/Cellar/openssl@3/3.1.1_1
You are replacing the current local value of build.puma, which is currently "--with-opt-dir=/usr/local/opt/openssl@1.1"

// bundle install
$ bundle install
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies......
Using rake 13.0.6
Using concurrent-ruby 1.2.2
Using thread_safe 0.3.6
Using minitest 5.18.1
Using builder 3.2.4
Using erubi 1.12.0
Using racc 1.7.1
Using crass 1.0.6
Using rack 2.2.7
Using nio4r 2.5.9
Using websocket-extensions 0.1.5
Using marcel 1.0.2
Using msgpack 1.7.1
Using bundler 2.2.17
Using byebug 11.1.3
Using matrix 0.4.2
Using regexp_parser 2.8.1
Using ffi 1.15.5
Using rb-fsevent 0.11.2
Using method_source 1.0.0
Using thor 1.2.2
Using rexml 3.2.5
Using rubyzip 2.3.2
Using tilt 2.2.0
Using websocket 1.2.9
Using spring 2.1.1
Using sqlite3 1.6.3 (x86_64-darwin)
Using turbolinks-source 5.2.0
Using i18n 1.14.1
Using tzinfo 1.2.11
Using nokogiri 1.15.3 (x86_64-darwin)
Using rack-test 2.1.0
Using sprockets 4.2.0
Using loofah 2.21.3
Fetching puma 4.3.12
Using rack-proxy 0.7.6
Using xpath 3.2.0
Using rb-inotify 0.10.1
Using sassc 2.4.0
Using selenium-webdriver 4.9.0
Using turbolinks 5.2.1
Using rails-html-sanitizer 1.6.0
Using mini_mime 1.1.2
Using bootsnap 1.16.0
Using date 3.3.3
Using zeitwerk 2.6.8
Using timeout 0.4.0
Using activesupport 6.0.6.1
Using listen 3.8.0
Using webdrivers 5.2.0
Using public_suffix 5.0.3
Using bindex 0.8.1
Using websocket-driver 0.7.5
Using rails-dom-testing 2.1.1
Using globalid 1.1.0
Using activemodel 6.0.6.1
Using net-protocol 0.2.1
Using addressable 2.8.4
Using spring-watcher-listen 2.0.1
Using actionview 6.0.6.1
Using activejob 6.0.6.1
Using activerecord 6.0.6.1
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using capybara 3.39.2
Using actionpack 6.0.6.1
Using mail 2.8.1
Using jbuilder 2.11.5
Using actioncable 6.0.6.1
Using activestorage 6.0.6.1
Using actionmailer 6.0.6.1
Using railties 6.0.6.1
Using sprockets-rails 3.4.2
Using actionmailbox 6.0.6.1
Using actiontext 6.0.6.1
Using sassc-rails 2.1.2
Using web-console 4.2.0
Using webpacker 4.3.0
Using rails 6.0.6.1
Using sass-rails 6.0.0
Installing puma 4.3.12 with native extensions
Bundle complete! 17 Gemfile dependencies, 81 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
```
