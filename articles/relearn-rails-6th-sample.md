---
title: "Rails の学び直し: 6th サンプルアプリケーション: 静的ぺーじ"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# 静的ページ

## アプリケーションの作成

```bash
$ rails _6.0.4_ new sample_app
      create
      create  README.md
      create  Rakefile
      create  .ruby-version
      create  config.ru
      create  .gitignore
      create  Gemfile
         run  git init from "."
Initialized empty Git repository in /Volumes/dev/git-dev/rails/sample_app/.git/
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
Resolving dependencies......
Using rake 13.0.6
Using concurrent-ruby 1.2.2
Using minitest 5.18.1
Using thread_safe 0.3.6
Using zeitwerk 2.6.8
Using builder 3.2.4
Using erubi 1.12.0
Using racc 1.7.1
Using crass 1.0.6
Using rack 2.2.7
Using nio4r 2.5.9
Using websocket-extensions 0.1.5
Using marcel 1.0.2
Using mini_mime 1.1.2
Using date 3.3.3
Using timeout 0.4.0
Using public_suffix 5.0.3
Using bindex 0.8.1
Using thor 1.2.2
Using rubyzip 2.3.2
Using tilt 2.2.0
Using websocket 1.2.9
Using regexp_parser 2.8.1
Using sqlite3 1.6.3 (x86_64-darwin)
Using turbolinks-source 5.2.0
Using i18n 1.14.1
Using tzinfo 1.2.11
Using nokogiri 1.15.3 (x86_64-darwin)
Using rack-test 2.1.0
Using bundler 2.2.17
Using websocket-driver 0.7.5
Using net-protocol 0.2.1
Using addressable 2.8.4
Using puma 4.3.12
Using sprockets 4.2.0
Using turbolinks 5.2.1
Using activesupport 6.0.6.1
Using msgpack 1.7.1
Using loofah 2.21.3
Using xpath 3.2.0
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using rails-html-sanitizer 1.6.0
Using mail 2.8.1
Using bootsnap 1.16.0
Using matrix 0.4.2
Using rack-proxy 0.7.6
Using byebug 11.1.3
Using spring 2.1.1
Using ffi 1.15.5
Using rb-fsevent 0.11.2
Using method_source 1.0.0
Using rexml 3.2.5
Using rails-dom-testing 2.1.1
Using globalid 1.1.0
Using activemodel 6.0.6.1
Using capybara 3.39.2
Using rb-inotify 0.10.1
Using sassc 2.4.0
Using actionview 6.0.6.1
Using activejob 6.0.6.1
Using actionpack 6.0.6.1
Using jbuilder 2.11.5
Using selenium-webdriver 4.9.0
Using actionmailer 6.0.6.1
Using railties 6.0.6.1
Using sprockets-rails 3.4.2
Using actioncable 6.0.6.1
Using web-console 4.2.0
Using webdrivers 5.2.0
Using webpacker 4.3.0
Using sassc-rails 2.1.2
Using activerecord 6.0.6.1
Using listen 3.8.0
Using activestorage 6.0.6.1
Using sass-rails 6.0.0
Using spring-watcher-listen 2.0.1
Using actionmailbox 6.0.6.1
Using actiontext 6.0.6.1
Using rails 6.0.6.1
Bundle complete! 17 Gemfile dependencies, 81 gems now installed.
Use `bundle info [gemname]` to see where a bundled gem is installed.
         run  bundle binstubs bundler
         run  bundle exec spring binstub --all
* bin/rake: Spring inserted
* bin/rails: Spring inserted
       rails  webpacker:install
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
      create  config/webpacker.yml
Copying webpack core config
      create  config/webpack
      create  config/webpack/development.js
      create  config/webpack/environment.js
      create  config/webpack/production.js
      create  config/webpack/test.js
Copying postcss.config.js to app root directory
      create  postcss.config.js
Copying babel.config.js to app root directory
      create  babel.config.js
Copying .browserslistrc to app root directory
      create  .browserslistrc
The JavaScript app source directory already exists
       apply  /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/webpacker-4.3.0/lib/install/binstubs.rb
  Copying binstubs
       exist    bin
      create    bin/webpack
      create    bin/webpack-dev-server
      append  .gitignore
Installing all JavaScript dependencies [4.3.0]
         run  yarn add @rails/webpacker@4.3.0 from "."
yarn add v1.22.19
info No lockfile found.
[1/4] 🔍  Resolving packages...
warning @rails/webpacker > node-sass > request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
warning @rails/webpacker > node-sass > node-gyp > request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
warning @rails/webpacker > compression-webpack-plugin > cacache > @npmcli/move-file@1.1.2: This functionality has been moved to @npmcli/fs
warning @rails/webpacker > node-sass > node-gyp > tar@2.2.2: This version of tar is no longer supported, and will not receive security updates. Please upgrade asap.
warning @rails/webpacker > node-sass > request > har-validator@5.1.5: this library is no longer supported
warning @rails/webpacker > node-sass > request > uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar@2.1.8: Chokidar 2 does not receive security updates since 2019. Upgrade to chokidar 3 with 15x fewer dependencies
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve@0.5.3: See https://github.com/lydell/source-map-resolve#deprecated
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar > fsevents@1.2.13: The v1 package contains DANGEROUS / INSECURE binaries. Upgrade to safe fsevents v2
warning @rails/webpacker > postcss-preset-env > postcss-color-gray > postcss-values-parser > flatten@1.0.3: flatten is deprecated in favor of utility frameworks such as lodash.
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo@1.3.2: This SVGO version is no longer supported. Upgrade to v2.x.x.
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo > stable@0.1.8: Modern JS already guarantees Array#sort() is a stable sort, so this library is deprecated. See the compatibility table on MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#browser_compatibility
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
[1/3] ⠈ fsevents
[2/3] ⠈ core-js
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents
Output:
node:events:491
      throw er; // Unhandled 'error' event
      ^

Error: spawn node-gyp ENOENT
    at ChildProcess._handle.onexit (node:internal/child_process:283:19)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)
Emitted 'error' event on ChildProcess instance at:
    at ChildProcess._handle.onexit (node:internal/child_process:289:12)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21) {
  errno: -2,
  code: 'ENOENT',
  syscall: 'spawn node-gyp',
  path: 'node-gyp',
  spawnargs: [ 'rebuild' ]
}

[-/3] ⢀ waiting...
[-/3] ⢀ waiting...
error /Volumes/dev/git-dev/rails/sample_app/node_modules/node-sass: Command failed.
Exit code: 1
Command: node scripts/build.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/sample_app/node_modules/node-sass
Output:
Building: /Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node /Volumes/dev/git-dev/rails/sample_app/node_modules/node-gyp/bin/node-gyp.js rebuild --verbose --libsass_ext= --libsass_cflags= --libsass_ldflags= --libsass_library=
gyp info it worked if it ends with ok
gyp verb cli [
gyp verb cli   '/Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node',
gyp verb cli   '/Volumes/dev/git-dev/rails/sample_app/node_modules/node-gyp/bin/node-gyp.js',
gyp verb cli   'rebuild',
gyp verb cli   '--verbose',
gyp verb cli   '--libsass_ext=',
gyp verb cli   '--libsass_cflags=',
gyp verb cli   '--libsass_ldflags=',
gyp verb cli   '--libsass_library='
gyp verb cli ]
gyp info using node-gyp@3.8.0
gyp info using node@18.16.0 | darwin | x64
gyp verb command rebuild []
gyp verb command clean []
gyp verb clean removing "build" directory
gyp verb command configure []
gyp verb check python checking for Python executable "python2" in the PATH
gyp verb `which` failed Error: not found: python2
gyp verb `which` failed     at getNotFoundError (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:13:12)
gyp verb `which` failed     at F (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:68:19)
gyp verb `which` failed     at E (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:80:29)
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:89:16
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/isexe/index.js:42:5
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/isexe/mode.js:8:5
gyp verb `which` failed     at FSReqCallback.oncomplete (node:fs:208:21)
gyp verb `which` failed  python2 Error: not found: python2
gyp verb `which` failed     at getNotFoundError (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:13:12)
gyp verb `which` failed     at F (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:68:19)
gyp verb `which` failed     at E (/Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:80:29)
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/which/which.js:89:16
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/isexe/index.js:42:5
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/sample_app/node_modules/isexe/mode.js:8:5
gyp verb `which` failed     at FSReqCallback.oncomplete (node:fs:208:21) {
gyp verb `which` failed   code: 'ENOENT'
gyp verb `which` failed }
gyp verb check python checking for Python executable "python" in the PATH
gyp verb `which` succeeded python /Users/glaciermelt/.pyenv/shims/python
gyp ERR! configure error
gyp ERR! stack Error: Command failed: /Users/glaciermelt/.pyenv/shims/python -c import sys; print "%s.%s.%s" % sys.version_info[:3];
gyp ERR! stack   File "<string>", line 1
gyp ERR! stack     import sys; print "%s.%s.%s" % sys.version_info[:3];
gyp ERR! stack                       ^
gyp ERR! stack SyntaxError: invalid syntax
gyp ERR! stack
gyp ERR! stack     at ChildProcess.exithandler (node:child_process:419:12)
gyp ERR! stack     at ChildProcess.emit (node:events:513:28)
gyp ERR! stack     at maybeClose (node:internal/child_process:1091:16)
gyp ERR! stack     at ChildProcess._handle.onexit (node:internal/child_process:302:5)
gyp ERR! System Darwin 21.6.0
gyp ERR! command "/Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node" "/Volumes/dev/git-dev/rails/sample_app/node_modules/node-gyp/bin/node-gyp.js" "rebuild" "--verbose" "--libsass_ext=" "--libsass_cflags=" "--libsass_ldflags=" "--libsass_library="
gyp ERR! cwd /Volumes/dev/git-dev/rails/sample_app/node_modules/node-sass
gyp ERR! node -v v18.16.0
gyp ERR! node-gyp -v v3.8.0
gyp ERR! not ok


Installing dev server for live reloading
         run  yarn add --dev webpack-dev-server from "."
yarn add v1.22.19
info No lockfile found.
[1/4] 🔍  Resolving packages...
warning webpack-dev-server > webpack-dev-middleware > memfs@3.6.0: this will be v4
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
success Saved 164 new dependencies.
info Direct dependencies
├ @rails/actioncable@6.1.7
├ @rails/activestorage@6.1.7
├ @rails/ujs@6.1.7
├ turbolinks@5.2.0
└ webpack-dev-server@4.15.1
info All dependencies
├ @leichtgewicht/ip-codec@2.0.4
├ @rails/actioncable@6.1.7
├ @rails/activestorage@6.1.7
├ @rails/ujs@6.1.7
├ @types/body-parser@1.19.2
├ @types/bonjour@3.5.10
├ @types/connect-history-api-fallback@1.5.0
├ @types/connect@3.4.35
├ @types/express-serve-static-core@4.17.35
├ @types/express@4.17.17
├ @types/http-errors@2.0.1
├ @types/http-proxy@1.17.11
├ @types/json-schema@7.0.12
├ @types/mime@3.0.1
├ @types/range-parser@1.2.4
├ @types/retry@0.12.0
├ @types/send@0.17.1
├ @types/serve-index@1.9.1
├ @types/serve-static@1.15.2
├ @types/sockjs@0.3.33
├ @types/ws@8.5.5
├ accepts@1.3.8
├ ajv-formats@2.1.1
├ ajv-keywords@5.1.0
├ ajv@8.12.0
├ ansi-html-community@0.0.8
├ anymatch@3.1.3
├ array-flatten@1.1.1
├ balanced-match@1.0.2
├ batch@0.6.1
├ binary-extensions@2.2.0
├ body-parser@1.20.1
├ bonjour-service@1.1.1
├ brace-expansion@1.1.11
├ braces@3.0.2
├ call-bind@1.0.2
├ chokidar@3.5.3
├ compressible@2.0.18
├ compression@1.7.4
├ concat-map@0.0.1
├ connect-history-api-fallback@2.0.0
├ content-disposition@0.5.4
├ cookie-signature@1.0.6
├ cookie@0.5.0
├ core-util-is@1.0.3
├ cross-spawn@7.0.3
├ default-gateway@6.0.3
├ define-lazy-prop@2.0.0
├ detect-node@2.1.0
├ dns-equal@1.0.0
├ dns-packet@5.6.0
├ ee-first@1.1.1
├ eventemitter3@4.0.7
├ execa@5.1.1
├ express@4.18.2
├ fast-deep-equal@3.1.3
├ faye-websocket@0.11.4
├ fill-range@7.0.1
├ finalhandler@1.2.0
├ follow-redirects@1.15.2
├ forwarded@0.2.0
├ fs-monkey@1.0.4
├ fs.realpath@1.0.0
├ fsevents@2.3.2
├ get-stream@6.0.1
├ glob-parent@5.1.2
├ glob@7.2.3
├ graceful-fs@4.2.11
├ handle-thing@2.0.1
├ has-proto@1.0.1
├ has-symbols@1.0.3
├ has@1.0.3
├ hpack.js@2.1.6
├ html-entities@2.4.0
├ http-deceiver@1.2.7
├ http-parser-js@0.5.8
├ http-proxy-middleware@2.0.6
├ http-proxy@1.18.1
├ human-signals@2.1.0
├ inflight@1.0.6
├ inherits@2.0.4
├ ipaddr.js@2.1.0
├ is-binary-path@2.1.0
├ is-docker@2.2.1
├ is-extglob@2.1.1
├ is-number@7.0.0
├ is-plain-obj@3.0.0
├ is-stream@2.0.1
├ is-wsl@2.2.0
├ isarray@1.0.0
├ isexe@2.0.0
├ json-schema-traverse@1.0.0
├ launch-editor@2.6.0
├ media-typer@0.3.0
├─ memfs@3.6.0
├ merge-descriptors@1.0.1
├ merge-stream@2.0.0
├ methods@1.1.2
├ micromatch@4.0.5
├ mime-db@1.52.0
├ mime-types@2.1.35
├ mime@1.6.0
├ mimic-fn@2.1.0
├ minimalistic-assert@1.0.1
├ minimatch@3.1.2
├ ms@2.0.0
├ multicast-dns@7.2.5
├ negotiator@0.6.3
├ node-forge@1.3.1
├ normalize-path@3.0.0
├ npm-run-path@4.0.1
├ object-inspect@1.12.3
├ obuf@1.1.2
├ on-headers@1.0.2
├ onetime@5.1.2
├ open@8.4.2
├ p-retry@4.6.2
├ path-is-absolute@1.0.1
├ path-key@3.1.1
├ path-to-regexp@0.1.7
├ picocolors@1.0.0
├ picomatch@2.3.1
├ process-nextick-args@2.0.1
├ proxy-addr@2.0.7
├ punycode@2.3.0
├ raw-body@2.5.1
├ readable-stream@3.6.2
├ readdirp@3.6.0
├ require-from-string@2.0.2
├ requires-port@1.0.0
├ retry@0.13.1
├ rimraf@3.0.2
├ safe-buffer@5.2.1
├ safer-buffer@2.1.2
├ select-hose@2.0.0
  selfsigned@2.1.1
├ serve-index@1.9.1
├ serve-static@1.15.0
├ shebang-command@2.0.0
├ shebang-regex@3.0.0
├ shell-quote@1.8.1
├ side-channel@1.0.4
├ signal-exit@3.0.7
├ sockjs@0.3.24
├ spark-md5@3.0.2
├ spdy-transport@3.0.0
├ spdy@4.0.2
├ string_decoder@1.3.0
├ strip-final-newline@2.0.0
├ thunky@1.1.0
├ to-regex-range@5.0.1
├ toidentifier@1.0.1
├ turbolinks@5.2.0
├ uri-js@4.4.1
├ util-deprecate@1.0.2
├ utils-merge@1.0.1
├ uuid@8.3.2
├ wbuf@1.7.3
├ webpack-dev-middleware@5.3.3
├ webpack-dev-server@4.15.1
├ websocket-driver@0.7.4
├ websocket-extensions@0.1.4
├ which@2.0.2
└ ws@8.13.0
✨  Done in 8.72s.
Webpacker successfully installed 🎉 🍰
```

## Gemfile 編集

```ruby
# Gemfile

source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.7.6'

gem 'rails',      '6.0.4'
gem 'puma',       '4.3.6'
gem 'sass-rails', '5.1.0'
gem 'webpacker',  '4.0.7'
gem 'turbolinks', '5.2.0'
gem 'jbuilder',   '2.9.1'
gem 'bootsnap',   '1.10.3', require: false

group :development, :test do
  gem 'sqlite3', '1.4.2'
  gem 'byebug',  '11.0.1', platforms: [:mri, :mingw, :x64_mingw]
end

group :development do
  gem 'web-console',           '4.0.1'
  gem 'listen',                '3.1.5'
  gem 'spring',                '2.1.0'
  gem 'spring-watcher-listen', '2.0.1'
end

group :test do
  gem 'capybara',                 '3.28.0'
  gem 'selenium-webdriver',       '3.142.4'
  gem 'webdrivers',               '4.1.2'
  gem 'rails-controller-testing', '1.0.4'
  gem 'minitest',                 '5.11.3'
  gem 'minitest-reporters',       '1.3.8'
  gem 'guard',                    '2.16.2'
  gem 'guard-minitest',           '2.4.6'
end

group :production do
  gem 'pg', '1.1.4'
end

# Windows ではタイムゾーン情報用の tzinfo-data gem を含める必要があります
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

```

## バンドルインストール

```bash
$ bundle _2.2.17_ config set --local without 'production'
$ bundle _2.2.17_ config
Settings are listed in order of priority. The top value will be used.
build.puma
Set for the current user (/Users/glaciermelt/.bundle/config): "--with-cflags=-Wno-error=implicit-function-declaration"

without
Set for your local app (/Volumes/dev/git-dev/rails/sample_app/.bundle/config): [:production]

$ bundle _2.2.17_ install
Fetching gem metadata from https://rubygems.org/...........
You have requested:
  listen = 3.1.5

The bundle currently has listen locked at 3.8.0.
Try running `bundle update listen`

If you are updating multiple gems in your Gemfile at once,
try passing them all to `bundle update`

$ bundle _2.2.17_ update
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies......
Using rake 12.3.3 (was 13.0.6)
Using concurrent-ruby 1.2.2
Using thread_safe 0.3.6
Using marcel 1.0.2
Using mini_mime 1.1.2
Using date 3.3.3
Using timeout 0.4.0
Using crass 1.0.6
Using rack 2.2.7
Using nio4r 2.5.9
Using websocket-extensions 0.1.5
Using bundler 2.2.17
Using zeitwerk 2.6.8
Using byebug 11.0.1 (was 11.1.3)
Using regexp_parser 1.8.2 (was 2.8.1)
Using childprocess 2.0.0
Fetching coderay 1.1.3
Using builder 3.2.4
Fetching ansi 1.5.0
Fetching formatador 1.1.0
Using msgpack 1.7.1
Using rb-fsevent 0.11.2
Fetching minitest 5.11.3 (was 5.18.1)
Using racc 1.7.1
Using public_suffix 5.0.3
Fetching lumberjack 1.2.8
Using bindex 0.8.1
Fetching shellany 0.0.1
Using ffi 1.15.5
Using method_source 1.0.0
Using thor 1.2.2
Fetching guard-compat 1.2.1
Using erubi 1.12.0
Fetching ruby-progressbar 1.13.0
Using ruby_dep 1.5.0
Using uri 0.12.2
Using rubyzip 1.3.0 (was 2.3.2)
Using tilt 2.2.0
Using spring 2.1.0 (was 2.1.1)
Using sqlite3 1.4.2 (was 1.6.3)
Using turbolinks-source 5.2.0
Using i18n 1.14.1
Using tzinfo 1.2.11
Using net-protocol 0.2.1
Using rack-test 2.1.0
Using puma 4.3.6 (was 4.3.12)
Using rack-proxy 0.7.6
Using sprockets 3.7.2 (was 4.2.0)
Using websocket-driver 0.7.5
Using bootsnap 1.10.3 (was 1.16.0)
Using nokogiri 1.15.3 (x86_64-darwin)
Using addressable 2.8.4
Using rb-inotify 0.10.1
Fetching nenv 0.3.0
Using loofah 2.21.3
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using xpath 3.2.0
Using listen 3.1.5 (was 3.8.0)
Using net-http 0.3.2
Using sass-listen 4.0.0
Using selenium-webdriver 3.142.4 (was 4.9.0)
Using turbolinks 5.2.0 (was 5.2.1)
Using rails-html-sanitizer 1.6.0
Using mail 2.8.1
Using capybara 3.28.0 (was 3.39.2)
Using sass 3.7.4
Using spring-watcher-listen 2.0.1
Using webdrivers 4.1.2 (was 5.2.0)
Installing formatador 1.1.0
Installing ansi 1.5.0
Installing shellany 0.0.1
Installing lumberjack 1.2.8
Installing guard-compat 1.2.1
Installing ruby-progressbar 1.13.0
Installing nenv 0.3.0
Installing coderay 1.1.3
Installing minitest 5.11.3 (was 5.18.1)
Fetching notiffany 0.1.3
Using activesupport 6.0.4 (was 6.0.6.1)
Fetching minitest-reporters 1.3.8
Using rails-dom-testing 2.1.1
Fetching guard-minitest 2.4.6
Using actionview 6.0.4 (was 6.0.6.1)
Using jbuilder 2.9.1 (was 2.11.5)
Using globalid 1.1.0
Using activemodel 6.0.4 (was 6.0.6.1)
Using activejob 6.0.4 (was 6.0.6.1)
Using activerecord 6.0.4 (was 6.0.6.1)
Using actionpack 6.0.4 (was 6.0.6.1)
Using actioncable 6.0.4 (was 6.0.6.1)
Using activestorage 6.0.4 (was 6.0.6.1)
Using actionmailer 6.0.4 (was 6.0.6.1)
Using railties 6.0.4 (was 6.0.6.1)
Using sprockets-rails 3.4.2
Fetching rails-controller-testing 1.0.4
Using actionmailbox 6.0.4 (was 6.0.6.1)
Using actiontext 6.0.4 (was 6.0.6.1)
Using sass-rails 5.1.0 (was 6.0.0)
Using web-console 4.0.1 (was 4.2.0)
Using webpacker 4.0.7 (was 4.3.0)
Using rails 6.0.4 (was 6.0.6.1)
Installing notiffany 0.1.3
Fetching pry 0.14.2
Installing guard-minitest 2.4.6
Installing rails-controller-testing 1.0.4
Installing pry 0.14.2
Fetching guard 2.16.2
Installing minitest-reporters 1.3.8
Installing guard 2.16.2
Bundle updated!
Gems in the group 'production' were not updated.
```

## Webpacker インストール

```bash
$ rails webpacker:install
    conflict  config/webpacker.yml
Overwrite /Volumes/dev/git-dev/rails/sample_app/config/webpacker.yml? (enter "h" for help) [Ynaqdhm] n
        skip  config/webpacker.yml
Copying webpack core config
       exist  config/webpack
   identical  config/webpack/development.js
   identical  config/webpack/environment.js
   identical  config/webpack/production.js
   identical  config/webpack/test.js
Copying postcss.config.js to app root directory
   identical  postcss.config.js
Copying babel.config.js to app root directory
    conflict  babel.config.js
Overwrite /Volumes/dev/git-dev/rails/sample_app/babel.config.js? (enter "h" for help) [Ynaqdhm] n
        skip  babel.config.js
Copying .browserslistrc to app root directory
   identical  .browserslistrc
The JavaScript app source directory already exists
       apply  /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/webpacker-4.0.7/lib/install/binstubs.rb
  Copying binstubs
       exist    bin
    conflict    bin/webpack
  Overwrite /Volumes/dev/git-dev/rails/sample_app/bin/webpack? (enter "h" for help) [Ynaqdhm] n
        skip    bin/webpack
    conflict    bin/webpack-dev-server
  Overwrite /Volumes/dev/git-dev/rails/sample_app/bin/webpack-dev-server? (enter "h" for help) [Ynaqdhm] n
        skip    bin/webpack-dev-server
File unchanged! Either the supplied flag value not found or the content has already been inserted!  .gitignore
Installing all JavaScript dependencies [4.0.7]
         run  yarn add @rails/webpacker from "."
yarn add v1.22.19
[1/4] 🔍  Resolving packages...
warning @rails/webpacker > compression-webpack-plugin > cacache > @npmcli/move-file@1.1.2: This functionality has been moved to @npmcli/fs
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar@2.1.8: Chokidar 2 does not receive security updates since 2019. Upgrade to chokidar 3 with 15x fewer dependencies
warning @rails/webpacker > postcss-preset-env > postcss-color-functional-notation > postcss-values-parser > flatten@1.0.3: flatten is deprecated in favor of utility frameworks such as lodash.
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve@0.5.3: See https://github.com/lydell/source-map-resolve#deprecated
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar > fsevents@1.2.13: The v1 package contains DANGEROUS / INSECURE binaries. Upgrade to safe fsevents v2
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo@1.3.2: This SVGO version is no longer supported. Upgrade to v2.x.x.
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo > stable@0.1.8: Modern JS already guarantees Array#sort() is a stable sort, so this library is deprecated. See the compatibility table on MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#browser_compatibility
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
[1/2] ⠠ fsevents
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents
Output:
node:events:491
      throw er; // Unhandled 'error' event
      ^

Error: spawn node-gyp ENOENT
    at ChildProcess._handle.onexit (node:internal/child_process:283:19)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)
Emitted 'error' event on ChildProcess instance at:
    at ChildProcess._handle.onexit (node:internal/child_process:289:12)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21) {
  errno: -2,
  code: 'ENOENT',
  syscall: 'spawn node-gyp',
  path: 'node-gyp',
  spawnargs: [ 'rebuild' ]
}

Node.js v18.16.0"
success Saved lockfile.
success Saved 518 new dependencies.
info Direct dependencies
└ @rails/webpacker@5.4.4
info All dependencies
├ @ampproject/remapping@2.2.1
├ @babel/code-frame@7.22.5
├ @babel/compat-data@7.22.9
├ @babel/core@7.22.9
├ @babel/generator@7.22.9
├ @babel/helper-builder-binary-assignment-operator-visitor@7.22.5
├ @babel/helper-string-parser@7.22.5
├ @babel/helper-wrap-function@7.22.9
├ @babel/helpers@7.22.6
├ @babel/highlight@7.22.5
├ @babel/plugin-bugfix-safari-id-destructuring-collision-in-function-expression@7.22.5
├ @babel/plugin-bugfix-v8-spread-parameters-in-optional-chaining@7.22.5
├ @babel/plugin-proposal-class-properties@7.18.6
├ @babel/plugin-proposal-object-rest-spread@7.20.7
├ @babel/plugin-proposal-private-property-in-object@7.21.0-placeholder-for-preset-env.2
├ @babel/plugin-proposal-unicode-property-regex@7.18.6
├ @babel/plugin-syntax-class-properties@7.12.13
├ @babel/plugin-syntax-import-assertions@7.22.5
├ @babel/plugin-syntax-import-attributes@7.22.5
├ @babel/plugin-syntax-import-meta@7.10.4
├ @babel/plugin-syntax-top-level-await@7.14.5
├ @babel/plugin-syntax-unicode-sets-regex@7.18.6
├ @babel/plugin-transform-arrow-functions@7.22.5
├ @babel/plugin-transform-async-generator-functions@7.22.7
├ @babel/plugin-transform-async-to-generator@7.22.5
├ @babel/plugin-transform-block-scoped-functions@7.22.5
├ @babel/plugin-transform-block-scoping@7.22.5
├ @babel/plugin-transform-class-properties@7.22.5
├ @babel/plugin-transform-class-static-block@7.22.5
├ @babel/plugin-transform-classes@7.22.6
├ @babel/plugin-transform-computed-properties@7.22.5
├ @babel/plugin-transform-destructuring@7.22.5
├ @babel/plugin-transform-dotall-regex@7.22.5
├ @babel/plugin-transform-duplicate-keys@7.22.5
├ @babel/plugin-transform-dynamic-import@7.22.5
├ @babel/plugin-transform-exponentiation-operator@7.22.5
├ @babel/plugin-transform-export-namespace-from@7.22.5
├ @babel/plugin-transform-for-of@7.22.5
├ @babel/plugin-transform-function-name@7.22.5
├ @babel/plugin-transform-json-strings@7.22.5
├ @babel/plugin-transform-literals@7.22.5
├ @babel/plugin-transform-logical-assignment-operators@7.22.5
├ @babel/plugin-transform-member-expression-literals@7.22.5
├ @babel/plugin-transform-modules-amd@7.22.5
├ @babel/plugin-transform-modules-commonjs@7.22.5
├ @babel/plugin-transform-modules-systemjs@7.22.5
├ @babel/plugin-transform-modules-umd@7.22.5
├ @babel/plugin-transform-named-capturing-groups-regex@7.22.5
├ @babel/plugin-transform-new-target@7.22.5
├ @babel/plugin-transform-nullish-coalescing-operator@7.22.5
├ @babel/plugin-transform-numeric-separator@7.22.5
├─ @babel/plugin-transform-object-rest-spread@7.22.5
├ @babel/plugin-transform-object-super@7.22.5
├ @babel/plugin-transform-optional-catch-binding@7.22.5
├ @babel/plugin-transform-optional-chaining@7.22.6
├ @babel/plugin-transform-private-methods@7.22.5
├ @babel/plugin-transform-private-property-in-object@7.22.5
├ @babel/plugin-transform-property-literals@7.22.5
├ @babel/plugin-transform-regenerator@7.22.5
├ @babel/plugin-transform-reserved-words@7.22.5
├ @babel/plugin-transform-runtime@7.22.9
├ @babel/plugin-transform-shorthand-properties@7.22.5
├ @babel/plugin-transform-spread@7.22.5
├ @babel/plugin-transform-sticky-regex@7.22.5
├ @babel/plugin-transform-template-literals@7.22.5
├ @babel/plugin-transform-typeof-symbol@7.22.5
├ @babel/plugin-transform-unicode-escapes@7.22.5
├ @babel/plugin-transform-unicode-property-regex@7.22.5
├ @babel/plugin-transform-unicode-regex@7.22.5
├ @babel/plugin-transform-unicode-sets-regex@7.22.5
├─ @babel/preset-en7.22.9
├ @babel/preset-modules@0.1.5
├ @babel/regjsgen@0.8.0
├ @babel/runtime@7.22.6
├ @babel/traverse@7.22.8
├ @gar/promisify@1.1.3
├ @jridgewell/resolve-uri@3.1.0
├ @jridgewell/set-array@1.1.2
├ @jridgewell/source-map@0.3.5
├ @jridgewell/sourcemap-codec@1.4.14
├ @nicolo-ribaudo/semver-v6@6.3.3
├ @npmcli/fs@1.1.1
├ @npmcli/move-file@1.1.2
├ @rails/webpacker@5.4.4
├ @types/parse-json@4.0.0
├ @types/q@1.5.5
├ @webassemblyjs/floating-point-hex-parser@1.9.0
├ @webassemblyjs/helper-code-frame@1.9.0
├ @webassemblyjs/helper-fsm@1.9.0
├ @webassemblyjs/helper-wasm-section@1.9.0
├ @webassemblyjs/wasm-edit@1.9.0
├ @webassemblyjs/wasm-opt@1.9.0
├ @xtuc/ieee754@1.2.0
├ acorn@6.4.2
├ aggregate-error@3.1.0
├ ajv-errors@1.0.1
├ ajv-keywords@3.5.2
├ ajv@6.12.6
├ ansi-regex@4.1.1
├ ansi-styles@3.2.1
├ argparse@1.0.10
├ arr-flatten@1.1.0
├ array.prototype.reduce@1.0.5
├ arraybuffer.prototype.slice@1.0.1
├ asn1.js@5.4.1
├ assert@1.5.0
├ assign-symbols@1.0.0
├ async-each@1.0.6
├ atob@2.1.2
├ autoprefixer@9.8.8
├ babel-loader@8.3.0
├ babel-plugin-dynamic-import-node@2.3.3
├ babel-plugin-macros@2.8.0
├ base@0.11.2
├ base64-js@1.5.1
├ bluebird@3.7.2
├ boolbase@1.0.0
├ braces@2.3.2
├ brorand@1.1.0
├ browserify-aes@1.2.0
├ browserify-cipher@1.0.1
├ browserify-des@1.0.2
├ browserify-rsa@4.1.0
├ browserify-sign@4.2.1
├ browserify-zlib@0.2.0
├ buffer-xor@1.0.3
├ buffer@4.9.2
├ builtin-status-codes@3.0.0
├ cache-base@1.0.1
├ caller-callsite@2.0.0
├ caller-path@2.0.0
├ callsites@2.0.0
├ camelcase@5.3.1
├ caniuse-lite@1.0.30001516
├ case-sensitive-paths-webpack-plugin@2.4.0
├─ chre-trace-event@1.0.3
├ class-utils@0.3.6
├ clean-stack@2.2.0
├ cliui@5.0.0
├ coa@2.0.2
├ collection-visit@1.0.0
├ color-convert@1.9.3
├ color-name@1.1.3
├ color-string@1.9.1
├ color@3.2.1
├ compression-webpack-plugin@4.0.1
├ concat-stream@1.6.2
├ console-browserify@1.2.0
├ constants-browserify@1.0.0
├ convert-source-map@1.9.0
├ copy-concurrently@1.0.5
├ copy-descriptor@0.1.1
├ core-js@3.31.1
├ create-ecdh@4.0.4
├ create-hmac@1.1.7
├ cross-spawn@6.0.5
├ crypto-browserify@3.12.0
├ css-blank-pseudo@0.1.4
├ css-color-names@0.0.4
├ css-declaration-sorter@4.0.1
├ css-has-pseudo@0.10.0
├ css-loader@3.6.0
├ css-prefers-color-scheme@3.1.1
├ css-select-base-adapter@0.1.1
├ css-select@2.1.0
├ css-tree@1.0.0-alpha.37
├ css-what@3.4.2
├ cssdb@4.4.0
├ cssnano-preset-default@4.0.8
├ cssnano-util-raw-cache@4.0.1
├─ cssno-util-same-parent@4.0.1
├ cssnano@4.1.11
├ csso@4.2.0
├ cyclist@1.0.2
├ decamelize@1.2.0
├ decode-uri-component@0.2.2
├ des.js@1.1.0
├ detect-file@1.0.0
├ diffie-hellman@5.0.3
├ dom-serializer@0.2.2
├ domain-browser@1.2.0
├ domelementtype@1.3.1
├ domutils@1.7.0
├ dot-prop@5.3.0
├ duplexify@3.7.1
├ electron-to-chromium@1.4.461
├ emoji-regex@7.0.3
├ enhanced-resolve@4.5.0
├ entities@2.2.0
├ errno@0.1.8
├ es-array-method-boxes-properly@1.0.0
├ es-set-tostringtag@2.0.1
├ es-to-primitive@1.2.1
├ escalade@3.1.1
├ escape-string-regexp@1.0.5
├ eslint-scope@4.0.3
├ esprima@4.0.1
├ esrecurse@4.3.0
├ estraverse@4.3.0
├ esutils@2.0.3
├ events@3.3.0
├ evp_bytestokey@1.0.3
├ expand-brackets@2.1.4
├ expand-tilde@2.0.2
├ extglob@2.0.4
├ fast-json-stable-stringify@2.1.0
├ file-loader@6.2.0
├─ fill-range@4.0
├ findup-sync@3.0.0
├ flatted@3.2.7
├ flatten@1.0.3
├ flush-write-stream@1.1.1
├ for-in@1.0.2
├ from2@2.3.0
├ function.prototype.name@1.1.5
├ functions-have-names@1.2.3
├ gensync@1.0.0-beta.2
├ get-caller-file@2.0.5
├ get-symbol-description@1.0.0
├ global-modules@2.0.0
├ global-prefix@3.0.0
├ globalthis@1.0.3
├ has-bigints@1.0.2
├ has-value@1.0.0
├ hash.js@1.1.7
├ hex-color-regex@1.1.0
├ hmac-drbg@1.0.1
├ hsl-regex@1.0.0
├ hsla-regex@1.0.0
├ https-browserify@1.0.0
├ icss-utils@4.1.1
├ ieee754@1.2.1
├ immutable@4.3.1
├ import-cwd@2.1.0
├ import-fresh@2.0.0
├ import-from@2.1.0
├ import-local@2.0.0
├ indent-string@4.0.0
├ infer-owner@1.0.4
├ ini@1.3.8
├ internal-slot@1.0.5
├ interpret@1.4.0
├ is-absolute-url@2.1.0
├ is-accessor-descriptor@1.0.0
├ is-arrayish@0.2.1
├ is-bigint@1.0.4
├ is-boolean-object@1.1.2
├ is-callable@1.2.7
├ is-color-stop@1.1.0
├ is-core-module@2.12.1
├ is-data-descriptor@1.0.0
├ is-date-object@1.0.5
├ is-descriptor@1.0.2
├ is-directory@0.3.1
├ is-fullwidth-code-point@2.0.0
├ is-negative-zero@2.0.2
├ is-number-object@1.0.7
├ is-obj@2.0.0
├ is-plain-object@2.0.4
├ is-resolvable@1.1.0
├ is-symbol@1.0.4
├ is-typed-array@1.1.10
├ is-weakref@1.0.2
├ is-windows@1.0.2
├ jest-worker@26.6.2
├ js-tokens@4.0.0
├ jsesc@2.5.2
├ json-parse-better-errors@1.0.2
├ json-parse-even-better-errors@2.3.1
├ json-schema-traverse@0.4.1
├ json5@2.2.3
├ klona@2.0.6
├ last-call-webpack-plugin@3.0.0
├ lines-and-columns@1.2.4
├ loader-runner@2.4.0
├ locate-path@3.0.0
├ lodash.debounce@4.0.8
├ lodash.get@4.4.2
├ lodash.has@4.5.2
├ lodash.memoize@4.1.2
├ lodash.uniq@4.5.0
├─ lodash@4.17.21
├ make-dir@3.1.0
├ map-visit@1.0.0
├ mdn-data@2.0.4
├ memory-fs@0.4.1
├ micromatch@3.1.10
├ miller-rabin@4.0.1
├ mini-css-extract-plugin@0.9.0
├ minimist@1.2.8
├ minipass-collect@1.0.2
├ minipass-flush@1.0.5
├ minipass-pipeline@1.2.4
├ minizlib@2.1.2
├ mississippi@3.0.0
├ mixin-deep@1.3.2
├ mkdirp@0.5.6
├ move-concurrently@1.0.1
├ nanomatch@1.2.13
├ neo-async@2.6.2
├ nice-try@1.0.5
├ node-libs-browser@2.2.1
├ node-releases@2.0.13
├ normalize-range@0.1.2
├ normalize-url@1.9.1
├ nth-check@1.0.2
├ num2fraction@1.2.2
├ object-assign@4.1.1
├ object-copy@0.1.0
├ object.assign@4.1.4
├ object.getownpropertydescriptors@2.1.6
├ object.values@1.1.6
├ optimize-css-assets-webpack-plugin@5.0.8
├ os-browserify@0.3.0
├ p-limit@2.3.0
├ p-locate@3.0.0
├ p-map@4.0.0
├ p-try@2.2.0
├ pako@1.0.11
├─ parall-transform@1.2.0
├ parent-module@1.0.1
├ parse-asn1@5.1.6
├ parse-json@4.0.0
├ parse-passwd@1.0.0
├ pascalcase@0.1.1
├ path-browserify@0.0.1
├ path-complete-extname@1.0.0
├ path-dirname@1.0.2
├ path-exists@3.0.0
├ path-parse@1.0.7
├ path-type@4.0.0
├ pify@2.3.0
├ pnp-webpack-plugin@1.7.0
├ posix-character-classes@0.1.1
├ postcss-attribute-case-insensitive@4.0.2
├ postcss-calc@7.0.5
├ postcss-color-functional-notation@2.0.1
├ postcss-color-gray@5.0.0
├ postcss-color-hex-alpha@5.0.3
├ postcss-color-mod-function@3.0.3
├ postcss-color-rebeccapurple@4.0.1
├ postcss-colormin@4.0.3
├ postcss-convert-values@4.0.1
├ postcss-custom-media@7.0.8
├ postcss-custom-properties@8.0.11
├ postcss-custom-selectors@5.1.2
├ postcss-dir-pseudo-class@5.0.0
├ postcss-discard-comments@4.0.2
├ postcss-discard-duplicates@4.0.2
├ postcss-discard-empty@4.0.1
├ postcss-discard-overridden@4.0.1
├ postcss-double-position-gradients@1.0.0
├ postcss-env-function@2.0.2
├ postcss-flexbugs-fixes@4.2.1
├ postcss-focus-visible@4.0.0
├ postcss-focus-within@3.0.0
├ postcss-font-variant@4.0.1
├ postcss-gap-properties@2.0.0
├ postcss-image-set-function@3.0.1
├ postcss-import@12.0.1
├ postcss-initial@3.0.4
├ postcss-lab-function@2.0.1
├ postcss-load-config@2.1.2
├ postcss-loader@3.0.0
├ postcss-logical@3.0.0
├ postcss-media-minmax@4.0.0
├ postcss-merge-longhand@4.0.11
├ postcss-merge-rules@4.0.3
├ postcss-minify-font-values@4.0.2
├ postcss-minify-gradients@4.0.2
├ postcss-minify-params@4.0.2
├ postcss-minify-selectors@4.0.2
├ postcss-modules-extract-imports@2.0.0
├ postcss-modules-local-by-default@3.0.3
├ postcss-modules-scope@2.2.0
├ postcss-modules-values@3.0.0
├ postcss-nesting@7.0.1
├─ postcss-normalize-charset.0.1
├ postcss-normalize-display-values@4.0.2
├ postcss-normalize-positions@4.0.2
├ postcss-normalize-repeat-style@4.0.2
├ postcss-normalize-string@4.0.2
├ postcss-normalize-timing-functions@4.0.2
├ postcss-normalize-unicode@4.0.1
├ postcss-normalize-url@4.0.1
├ postcss-normalize-whitespace@4.0.2
├ postcss-ordered-values@4.1.2
├ postcss-overflow-shorthand@2.0.0
├ postcss-page-break@2.0.0
├ postcss-place@4.0.1
├ postcss-preset-env@6.7.1
├ postcss-pseudo-class-any-link@6.0.0
├ postcss-reduce-initial@4.0.3
├ postcss-reduce-transforms@4.0.2
├ postcss-replace-overflow-wrap@3.0.0
├ postcss-safe-parser@4.0.2
├ postcss-selector-matches@4.0.0
├ postcss-selector-not@4.0.1
├ postcss-svgo@4.0.3
├ postcss-unique-selectors@4.0.1
├ prepend-http@1.0.4
├ process@0.11.10
├ prr@1.0.1
├ public-encrypt@4.0.3
├ pump@3.0.0
├ pumpify@1.5.1
├ punycode@1.4.1
  q@1.5.1
├ query-string@4.3.4
├ querystring-es3@0.2.1
├ randomfill@1.0.4
├ read-cache@1.0.0
├ regenerate-unicode-properties@10.1.0
├ regenerator-runtime@0.13.11
├ regenerator-transform@0.15.1
├ regexp.prototype.flags@1.5.0
├ regexpu-core@5.3.2
├ regjsparser@0.9.1
├ remove-trailing-separator@1.1.0
├ repeat-element@1.1.4
├ require-directory@2.1.1
├ require-main-filename@2.0.0
├ resolve-cwd@2.0.0
├ resolve-dir@1.0.1
├ resolve-url@0.2.1
├ resolve@1.22.2
├ ret@0.1.15
├ rgb-regex@1.0.1
├ rgba-regex@1.0.0
├ run-queue@1.0.3
├ safe-regex-test@1.0.0
├ sass-loader@10.1.1
├ sass@1.63.6
├ sax@1.2.4
├ set-blocking@2.0.0
├ set-value@2.0.1
├ setimmediate@1.0.5
├ shebang-command@1.2.0
├ shebang-regex@1.0.0
├ simple-swizzle@0.2.2
├ snapdragon-node@2.1.1
├ snapdragon-util@3.0.1
├ sort-keys@1.1.2
├ source-list-map@2.0.1
├ source-map-js@1.0.2
├ source-map-resolve@0.5.3
├ source-map-support@0.5.21
├ source-map-url@0.4.1
├─ split-string@3.1.0
├─ sprintf-js@1.0.3
├─ ssri@8.0.1
├─ stable@0.1.8
├─ static-extend@0.1.2
├─ stream-browserify@2.0.2
├─ stream-each@1.2.3
├─ stream-http@2.8.3
├─ strict-uri-encode@1.1.0
├─ string.prototype.trim@1.2.7
├─ string.prototype.trimend@1.0.6
├─ string.prototype.trimstart@1.0.6
├─ strip-ansi@5.2.0
├─ style-loader@1.3.0
├─ stylehacks@4.0.3
├─ supports-color@6.1.0
├─ supports-preserve-symlinks-flag@1.0.0
├─ svgo@1.3.2
├─ tar@6.1.15
├─ terser-webpack-plugin@4.2.3
├─ terser@5.19.0
├─ through2@2.0.5
├─ timers-browserify@2.0.12
├─ timsort@0.3.0
├─ to-arraybuffer@1.0.1
├─ to-fast-properties@2.0.0
├─ to-object-path@0.3.0
├─ to-regex-range@2.1.1
├─ ts-pnp@1.2.0
├─ tty-browserify@0.0.0
├─ typed-array-buffer@1.0.0
├─ typed-array-byte-length@1.0.0
├─ typed-array-byte-offset@1.0.0
├─ typed-array-length@1.0.4
├─ typedarray@0.0.6
├─ unbox-primitive@1.0.2
├─ unicode-canonical-property-names-ecmascript@2.0.0
├─ unicode-match-property-ecmascript@2.0.0
├─ unicode-match-property-value-ecmascript@2.1.0
├─ unicode-property-aliases-ecmascript@2.1.0
├─ union-value@1.0.1
├─ unique-slug@2.0.2
├─ unquote@1.1.1
├─ unset-value@1.0.0
├─ upath@1.2.0
├─ update-browserslist-db@1.0.11
├─ urix@0.1.0
├─ url@0.11.1
├─ use@3.1.1
├─ util.promisify@1.0.1
├─ util@0.11.1
├─ v8-compile-cache@2.3.0
├─ vendors@1.0.4
├─ vm-browserify@1.1.2
├─ watchpack-chokidar2@2.0.1
├─ watchpack@1.7.5
├─ webpack-assets-manifest@3.1.1
├─ webpack-cli@3.3.12
├─ webpack@4.46.0
├─ which-boxed-primitive@1.0.2
├─ which-module@2.0.1
├─ which-typed-array@1.1.10
├─ which@1.3.1
├─ worker-farm@1.7.0
├─ wrap-ansi@5.1.0
├─ xtend@4.0.2
├─ yaml@1.10.2
├─ yargs-parser@13.1.2
├─ yargs@13.3.2
└─ yocto-queue@0.1.0
✨  Done in 13.03s.
Installing dev server for live reloading
         run  yarn add --dev webpack-dev-server from "."
yarn add v1.22.19
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/sample_app/node_modules/watchpack-chokidar2/node_modules/fsevents
Output:
node:events:491
      throw er; // Unhandled 'error' event
      ^

Error: spawn node-gyp ENOENT
    at ChildProcess._handle.onexit (node:internal/child_process:283:19)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21)
Emitted 'error' event on ChildProcess instance at:
    at ChildProcess._handle.onexit (node:internal/child_process:289:12)
    at onErrorNT (node:internal/child_process:476:16)
    at process.processTicksAndRejections (node:internal/process/task_queues:82:21) {
  errno: -2,
  code: 'ENOENT',
  syscall: 'spawn node-gyp',
  path: 'node-gyp',
  spawnargs: [ 'rebuild' ]
}

Node.js v18.16.0"
info This module is OPTIONAL, you can safely ignore this error
success Saved 1 new dependency.
info Direct dependencies
└─ webpack-dev-server@4.15.1
info All dependencies
└─ webpack-dev-server@4.15.1
✨  Done in 2.51s.
Webpacker successfully installed 🎉 🍰
```

## README のアップデート

```markdown
# Ruby on Rails チュートリアルのサンプルアプリケーション

これは、次の教材で作られたサンプルアプリケーションです。
[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
（第6版）
[Michael Hartl](https://www.michaelhartl.com/) 著

## ライセンス

[Ruby on Rails チュートリアル](https://railstutorial.jp/)内にある
ソースコードはMITライセンスとBeerwareライセンスのもとで公開されています。
詳細は [LICENSE.md](LICENSE.md) をご覧ください。

## 使い方

このアプリケーションを動かす場合は、まずはリポジトリを手元にクローンしてください。
その後、次のコマンドで必要になる RubyGems をインストールします。

```
$ gem install bundler -v 2.2.17
$ bundle _2.2.17_ config set --local without 'production'
$ bundle _2.2.17_ install
```

その後、データベースへのマイグレーションを実行します。

```
$ rails db:migrate
```

最後に、テストを実行してうまく動いているかどうか確認してください。

```
$ rails test
```

テストが無事に通ったら、Railsサーバーを立ち上げる準備が整っているはずです。

```
$ rails server
```

詳しくは、[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
を参考にしてください。

```

## ローカルサーバーへの接続を許可する

```ruby
# config/environments/development.rb

Rails.application.configure do
  ...
  # ローカルサーバーへの接続を許可する
  config.hosts.clear
end
```

## Application コントローラに hello アクションを追加する

```ruby
# app/controllers/application_controller.rb

class ApplicationController < ActionController::Base

  def hello
    render html: "hello, world!"
  end
end
```

## ルートルーティングの設定

```ruby
# config/routes.rb

Rails.application.routes.draw do
  root 'application#hello'
end
```

## Heroku にプッシュ

```bash
// Heroku アプリを作成
$ heroku create
Creating app... done, ⬢ shrouded-retreat-16411
https://shrouded-retreat-16411-3aeb990f1140.herokuapp.com/ | https://git.heroku.com/shrouded-retreat-16411.git

// Heroku のスタックを heroku-20 に設定
$ heroku stack:set heroku-20
Setting stack to heroku-20... done

// Heroku にプッシュ
$ git push heroku main
Enumerating objects: 117, done.
Counting objects: 100% (117/117), done.
Delta compression using up to 10 threads
Compressing objects: 100% (99/99), done.
Writing objects: 100% (117/117), 159.88 KiB | 10.66 MiB/s, done.
Total 117 (delta 9), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (9/9), done.
remote: Updated 92 paths from 3ca2216
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
remote: !       Push rejected to shrouded-retreat-16411.
remote:
To https://git.heroku.com/shrouded-retreat-16411.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://git.heroku.com/shrouded-retreat-16411.git'

// ローカルの Gemfile.lock に x86_64-linux を追加
$ bundle lock --add-platform x86_64-linux
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies...
Writing lockfile to /Volumes/dev/git-dev/rails/sample_app/Gemfile.lock

// 再度、Heroku にプッシュ
$ git push heroku main
Enumerating objects: 120, done.
Counting objects: 100% (120/120), done.
Delta compression using up to 10 threads
Compressing objects: 100% (102/102), done.
Writing objects: 100% (120/120), 160.14 KiB | 10.01 MiB/s, done.
Total 120 (delta 11), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (11/11), done.
remote: Updated 92 paths from f3a0232
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
remote:        Fetching minitest 5.11.3
remote:        Fetching thread_safe 0.3.6
remote:        Fetching concurrent-ruby 1.2.2
remote:        Installing zeitwerk 2.6.8
remote:        Installing minitest 5.11.3
remote:        Fetching builder 3.2.4
remote:        Installing concurrent-ruby 1.2.2
remote:        Installing thread_safe 0.3.6
remote:        Installing builder 3.2.4
remote:        Fetching erubi 1.12.0
remote:        Fetching racc 1.7.1
remote:        Installing erubi 1.12.0
remote:        Fetching crass 1.0.6
remote:        Fetching rack 2.2.7
remote:        Installing racc 1.7.1 with native extensions
remote:        Installing crass 1.0.6
remote:        Fetching nio4r 2.5.9
remote:        Installing rack 2.2.7
remote:        Fetching websocket-extensions 0.1.5
remote:        Installing nio4r 2.5.9 with native extensions
remote:        Installing websocket-extensions 0.1.5
remote:        Fetching marcel 1.0.2
remote:        Fetching mini_mime 1.1.2
remote:        Installing mini_mime 1.1.2
remote:        Installing marcel 1.0.2
remote:        Fetching timeout 0.4.0
remote:        Fetching date 3.3.3
remote:        Installing timeout 0.4.0
remote:        Installing date 3.3.3 with native extensions
remote:        Fetching msgpack 1.7.1
remote:        Installing msgpack 1.7.1 with native extensions
remote:        Using bundler 2.3.25
remote:        Fetching ffi 1.15.5
remote:        Installing ffi 1.15.5 with native extensions
remote:        Fetching method_source 1.0.0
remote:        Installing method_source 1.0.0
remote:        Fetching uri 0.12.2
remote:        Installing uri 0.12.2
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
remote:        Fetching net-http 0.3.2
remote:        Installing net-http 0.3.2
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
remote:        Fetching rb-inotify 0.10.1
remote:        Installing loofah 2.21.3
remote:        Fetching rails-dom-testing 2.1.1
remote:        Installing rails-dom-testing 2.1.1
remote:        Installing rb-inotify 0.10.1
remote:        Fetching globalid 1.1.0
remote:        Fetching activemodel 6.0.4
remote:        Installing globalid 1.1.0
remote:        Installing activemodel 6.0.4
remote:        Fetching jbuilder 2.9.1
remote:        Fetching mail 2.8.1
remote:        Installing jbuilder 2.9.1
remote:        Fetching rails-html-sanitizer 1.6.0
remote:        Installing mail 2.8.1
remote:        Installing rails-html-sanitizer 1.6.0
remote:        Fetching sass-listen 4.0.0
remote:        Installing sass-listen 4.0.0
remote:        Fetching activejob 6.0.4
remote:        Installing activejob 6.0.4
remote:        Fetching activerecord 6.0.4
remote:        Fetching actionview 6.0.4
remote:        Installing activerecord 6.0.4
remote:        Installing actionview 6.0.4
remote:        Fetching sass 3.7.4
remote:        Installing sass 3.7.4
remote:        Fetching actionpack 6.0.4
remote:        Installing actionpack 6.0.4
remote:        Fetching activestorage 6.0.4
remote:        Fetching actioncable 6.0.4
remote:        Installing activestorage 6.0.4
remote:        Installing actioncable 6.0.4
remote:        Fetching railties 6.0.4
remote:        Fetching actionmailer 6.0.4
remote:        Installing railties 6.0.4
remote:        Installing actionmailer 6.0.4
remote:        Fetching sprockets-rails 3.4.2
remote:        Installing sprockets-rails 3.4.2
remote:        Fetching actionmailbox 6.0.4
remote:        Installing actionmailbox 6.0.4
remote:        Fetching actiontext 6.0.4
remote:        Installing actiontext 6.0.4
remote:        Fetching rails 6.0.4
remote:        Fetching sass-rails 5.1.0
remote:        Installing sass-rails 5.1.0
remote:        Fetching webpacker 4.0.7
remote:        Installing webpacker 4.0.7
remote:        Installing rails 6.0.4
remote:        Bundle complete! 24 Gemfile dependencies, 66 gems now installed.
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
remote:        Bundle completed (28.82s)
remote:        Cleaning up the bundler cache.
remote: -----> Installing node-v16.18.1-linux-x64
remote: -----> Installing yarn-v1.22.19
remote: -----> Detecting rake tasks
remote: -----> Preparing app for Rails asset pipeline
remote:        Running: rake assets:precompile
remote:        yarn install v1.22.19
remote:        [1/4] Resolving packages...
remote:        [2/4] Fetching packages...
remote:        [3/4] Linking dependencies...
remote:        warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
remote:        [4/4] Building fresh packages...
remote:        Done in 13.98s.
remote:        I, [2023-07-17T08:44:03.791467 #1085]  INFO -- : Writing /tmp/build_2d6bcc16/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css
remote:        I, [2023-07-17T08:44:03.791945 #1085]  INFO -- : Writing /tmp/build_2d6bcc16/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css.gz
remote:        Compiling
remote:        Compiled all packs in /tmp/build_2d6bcc16/public/packs
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
remote:        Hash: f1847d946e62dc1e6545
remote:        Version: webpack 4.46.0
remote:        Time: 3340ms
remote:        Built at: 07/17/2023 8:44:09 AM
remote:                                                Asset       Size  Chunks                         Chunk Names
remote:               js/application-e90c885fb97a16cc2fae.js   68.2 KiB       0  [emitted] [immutable]  application
remote:            js/application-e90c885fb97a16cc2fae.js.br   15.2 KiB          [emitted]
remote:            js/application-e90c885fb97a16cc2fae.js.gz   17.5 KiB          [emitted]
remote:           js/application-e90c885fb97a16cc2fae.js.map    204 KiB       0  [emitted] [dev]        application
remote:        js/application-e90c885fb97a16cc2fae.js.map.br   43.4 KiB          [emitted]
remote:        js/application-e90c885fb97a16cc2fae.js.map.gz   50.1 KiB          [emitted]
remote:                                        manifest.json  364 bytes          [emitted]
remote:                                     manifest.json.br  128 bytes          [emitted]
remote:                                     manifest.json.gz  142 bytes          [emitted]
remote:        Entrypoint application = js/application-e90c885fb97a16cc2fae.js js/application-e90c885fb97a16cc2fae.js.map
remote:        [0] ./app/javascript/packs/application.js 742 bytes {0} [built]
remote:        [4] ./app/javascript/channels/index.js 205 bytes {0} [built]
remote:        [5] ./app/javascript/channels sync _channel\.js$ 160 bytes {0} [built]
remote:            + 3 hidden modules
remote:
remote:        Asset precompilation completed (20.98s)
remote:        Cleaning assets
remote:        Running: rake assets:clean
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
remote:        Done: 79.2M
remote: -----> Launching...
remote:  !     The following add-ons were automatically provisioned: heroku-postgresql. These add-ons may incur additional cost, which is prorated to the second. Run `heroku addons` for more info.
remote:        Released v7
remote:        https://shrouded-retreat-16411-3aeb990f1140.herokuapp.com/ deployed to Heroku
remote:
remote: This app is using the Heroku-20 stack, however a newer stack is available.
remote: To upgrade to Heroku-22, see:
remote: https://devcenter.heroku.com/articles/upgrading-to-the-latest-stack
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/shrouded-retreat-16411.git
 * [new branch]      main -> main
```

## Heroku のログを表示する

```bash
$ heroku logs --tail
2023-07-17T08:40:37.374123+00:00 app[api]: Initial release by user glacier-melt@hotmail.co.jp
2023-07-17T08:40:37.374123+00:00 app[api]: Release v1 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:40:37.509318+00:00 app[api]: Release v2 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:40:37.509318+00:00 app[api]: Enable Logplex by user glacier-melt@hotmail.co.jp
2023-07-17T08:41:20.275332+00:00 app[api]: Stack changed from heroku-22 to heroku-20 by user glacier-melt@hotmail.co.jp
2023-07-17T08:41:20.289160+00:00 app[api]: Release v3 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:41:20.289160+00:00 app[api]: Upgrade stack to heroku-20 by user glacier-melt@hotmail.co.jp
2023-07-17T08:41:40.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-17T08:41:43.000000+00:00 app[api]: Build failed -- check your build output: https://dashboard.heroku.com/apps/270149df-d54b-4785-9650-854a1da72e93/activity/builds/aac64e95-28c4-4ceb-b9cb-4af2a378bd26
2023-07-17T08:43:13.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:18.674687+00:00 app[api]: Release v4 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:18.674687+00:00 app[api]: Set LANG, RACK_ENV, RAILS_ENV, RAILS_LOG_TO_STDOUT, RAILS_SERVE_STATIC_FILES, SECRET_KEY_BASE config vars by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.512238+00:00 app[api]: Attach DATABASE (@ref:postgresql-flexible-35202) by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.512238+00:00 app[api]: Running release v5 commands by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.523741+00:00 app[api]: @ref:postgresql-flexible-35202 completed provisioning, setting DATABASE_URL. by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.523741+00:00 app[api]: Release v6 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.888969+00:00 app[api]: Release v7 created by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.888969+00:00 app[api]: Deploy 0b0e75c1 by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:19.903361+00:00 app[api]: Scaled to console@0:Basic rake@0:Basic web@1:Basic by user glacier-melt@hotmail.co.jp
2023-07-17T08:44:22.000000+00:00 app[api]: Build succeeded
2023-07-17T08:44:23.999562+00:00 heroku[web.1]: Starting process with command `bin/rails server -p ${PORT:-5000} -e production`
2023-07-17T08:44:26.256970+00:00 app[web.1]: => Booting Puma
2023-07-17T08:44:26.257005+00:00 app[web.1]: => Rails 6.0.4 application starting in production
2023-07-17T08:44:26.257006+00:00 app[web.1]: => Run `rails server --help` for more startup options
2023-07-17T08:44:26.935000+00:00 app[web.1]: Puma starting in single mode...
2023-07-17T08:44:26.935034+00:00 app[web.1]: * Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
2023-07-17T08:44:26.935035+00:00 app[web.1]: * Min threads: 5, max threads: 5
2023-07-17T08:44:26.935036+00:00 app[web.1]: * Environment: production
2023-07-17T08:44:26.935159+00:00 app[web.1]: * Listening on tcp://0.0.0.0:52928
2023-07-17T08:44:26.935325+00:00 app[web.1]: Use Ctrl-C to stop
2023-07-17T08:44:27.165709+00:00 heroku[web.1]: State changed from starting to up
2023-07-17T08:45:24.517722+00:00 app[web.1]: I, [2023-07-17T08:45:24.517668 #2]  INFO -- : [c03bb126-8fa1-4749-a0ad-a0ad7f2ff368] Started GET "/" for 217.178.26.43 at 2023-07-17 08:45:24 +0000
2023-07-17T08:45:24.519086+00:00 app[web.1]: I, [2023-07-17T08:45:24.519019 #2]  INFO -- : [c03bb126-8fa1-4749-a0ad-a0ad7f2ff368] Processing by ApplicationController#hello as HTML
2023-07-17T08:45:24.521693+00:00 app[web.1]: I, [2023-07-17T08:45:24.521659 #2]  INFO -- : [c03bb126-8fa1-4749-a0ad-a0ad7f2ff368]   Rendering html template
2023-07-17T08:45:24.521779+00:00 app[web.1]: I, [2023-07-17T08:45:24.521756 #2]  INFO -- : [c03bb126-8fa1-4749-a0ad-a0ad7f2ff368]   Rendered html template (Duration: 0.0ms | Allocations: 5)
2023-07-17T08:45:24.522065+00:00 app[web.1]: I, [2023-07-17T08:45:24.522042 #2]  INFO -- : [c03bb126-8fa1-4749-a0ad-a0ad7f2ff368] Completed 200 OK in 3ms (Views: 0.5ms | Allocations: 540)
2023-07-17T08:45:24.523306+00:00 heroku[router]: at=info method=GET path="/" host=shrouded-retreat-16411-3aeb990f1140.herokuapp.com request_id=c03bb126-8fa1-4749-a0ad-a0ad7f2ff368 fwd="217.178.26.43" dyno=web.1 connect=0ms service=6ms status=200 bytes=512 protocol=https
2023-07-17T08:45:24.816505+00:00 heroku[router]: at=info method=GET path="/favicon.ico" host=shrouded-retreat-16411-3aeb990f1140.herokuapp.com request_id=3440d191-2040-49a1-a6ee-5ab7143dc9aa fwd="217.178.26.43" dyno=web.1 connect=0ms service=5ms status=200 bytes=143 protocol=https
2023-07-17T08:45:26.312487+00:00 app[web.1]: I, [2023-07-17T08:45:26.312420 #2]  INFO -- : [6ef92702-367e-4531-9851-3b354fe05b3e] Started GET "/" for 210.139.253.4 at 2023-07-17 08:45:26 +0000
2023-07-17T08:45:26.313043+00:00 app[web.1]: I, [2023-07-17T08:45:26.313006 #2]  INFO -- : [6ef92702-367e-4531-9851-3b354fe05b3e] Processing by ApplicationController#hello as HTML
2023-07-17T08:45:26.313522+00:00 app[web.1]: I, [2023-07-17T08:45:26.313493 #2]  INFO -- : [6ef92702-367e-4531-9851-3b354fe05b3e]   Rendering html template
2023-07-17T08:45:26.313576+00:00 app[web.1]: I, [2023-07-17T08:45:26.313558 #2]  INFO -- : [6ef92702-367e-4531-9851-3b354fe05b3e]   Rendered html template (Duration: 0.0ms | Allocations: 3)
2023-07-17T08:45:26.313689+00:00 app[web.1]: I, [2023-07-17T08:45:26.313670 #2]  INFO -- : [6ef92702-367e-4531-9851-3b354fe05b3e] Completed 200 OK in 1ms (Views: 0.3ms | Allocations: 234)
2023-07-17T08:45:26.314652+00:00 heroku[router]: at=info method=GET path="/" host=shrouded-retreat-16411-3aeb990f1140.herokuapp.com request_id=6ef92702-367e-4531-9851-3b354fe05b3e fwd="210.139.253.4" dyno=web.1 connect=0ms service=3ms status=200 bytes=512 protocol=https
```

## 静的なページの生成

```bash
$ rails generate controller StaticPages home help
Running via Spring preloader in process 70329
      create  app/controllers/static_pages_controller.rb
       route  get 'static_pages/home'
              get 'static_pages/help'
      invoke  erb
      create    app/views/static_pages
      create    app/views/static_pages/home.html.erb
      create    app/views/static_pages/help.html.erb
      invoke  test_unit
      create    test/controllers/static_pages_controller_test.rb
      invoke  helper
      create    app/helpers/static_pages_helper.rb
      invoke    test_unit
      invoke  assets
      invoke    scss
      create      app/assets/stylesheets/static_pages.scss
```

## Node バージョンの調整

```bash
// node 14 にダウングレード
$ nvm use lts/fermium
Now using node v14.21.3 (npm v6.14.18)
glaciermelt (i386):/Volumes/dev/git-dev/rails/sample_app (feature/2023-07-17-static-pages|✚1)$ bundle _2.2.17_ update
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies........
Using rake 12.3.3
Using concurrent-ruby 1.2.2
Using minitest 5.11.3
Using thread_safe 0.3.6
Using zeitwerk 2.6.8
Using builder 3.2.4
Using erubi 1.12.0
Using racc 1.7.1
Using crass 1.0.6
Using rack 2.2.7
Using bindex 0.8.1
Using websocket-extensions 0.1.5
Using marcel 1.0.2
Using bundler 2.2.17
Using byebug 11.0.1
Using regexp_parser 1.8.2
Using childprocess 2.0.0
Using coderay 1.1.3
Using ffi 1.15.5
Using formatador 1.1.0
Using rb-fsevent 0.11.2
Using ruby_dep 1.5.0
Using lumberjack 1.2.8
Using nenv 0.3.0
Using shellany 0.0.1
Using method_source 1.0.0
Using thor 1.2.2
Using guard-compat 1.2.1
Using ruby-progressbar 1.13.0
Using uri 0.12.2
Using rubyzip 1.3.0
Using tilt 2.2.0
Using spring 2.1.0
Using sqlite3 1.4.2
Using turbolinks-source 5.2.0
Using i18n 1.14.1
Using tzinfo 1.2.11
Using nokogiri 1.15.3 (x86_64-darwin)
Using rack-test 2.1.0
Using rack-proxy 0.7.6
Using sprockets 3.7.2
Using mini_mime 1.1.2
Using date 3.3.3
Using activesupport 6.0.4
Using public_suffix 5.0.3
Using loofah 2.21.3
Using websocket-driver 0.7.5
Using xpath 3.2.0
Using rb-inotify 0.10.1
Using notiffany 0.1.3
Using pry 0.14.2
Using guard-minitest 2.4.6
Using net-http 0.3.2
Using selenium-webdriver 3.142.4
Using turbolinks 5.2.0
Using timeout 0.4.0
Using ansi 1.5.0
Using rails-html-sanitizer 1.6.0
Using net-protocol 0.2.1
Using listen 3.1.5
Using sass-listen 4.0.0
Using webdrivers 4.1.2
Using msgpack 1.7.1
Using nio4r 2.5.9
Using rails-dom-testing 2.1.1
Using globalid 1.1.0
Using activemodel 6.0.4
Using net-imap 0.3.6
Using net-pop 0.1.2
Using net-smtp 0.3.3
Using addressable 2.8.4
Using bootsnap 1.10.3
Using guard 2.16.2
Using jbuilder 2.9.1
Using minitest-reporters 1.3.8
Using puma 4.3.6
Using sass 3.7.4
Using spring-watcher-listen 2.0.1
Using actionview 6.0.4
Using activejob 6.0.4
Using activerecord 6.0.4
Using mail 2.8.1
Using capybara 3.28.0
Using actionpack 6.0.4
Using actioncable 6.0.4
Using activestorage 6.0.4
Using actionmailer 6.0.4
Using railties 6.0.4
Using actionmailbox 6.0.4
Using actiontext 6.0.4
Using rails-controller-testing 1.0.4
Using sprockets-rails 3.4.2
Using web-console 4.0.1
Using webpacker 4.0.7
Using rails 6.0.4
Using sass-rails 5.1.0
Bundle updated!
Gems in the group 'production' were not updated.

// yarn install
$ yarn install
yarn install v1.22.19
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
✨  Done in 10.96s.

// webpacker のインストール
$ rails webpacker:install
    conflict  config/webpacker.yml
Overwrite /Volumes/dev/git-dev/rails/sample_app/config/webpacker.yml? (enter "h" for help) [Ynaqdhm] n
        skip  config/webpacker.yml
Copying webpack core config
       exist  config/webpack
   identical  config/webpack/development.js
   identical  config/webpack/environment.js
   identical  config/webpack/production.js
   identical  config/webpack/test.js
Copying postcss.config.js to app root directory
   identical  postcss.config.js
Copying babel.config.js to app root directory
    conflict  babel.config.js
Overwrite /Volumes/dev/git-dev/rails/sample_app/babel.config.js? (enter "h" for help) [Ynaqdhm] n
        skip  babel.config.js
Copying .browserslistrc to app root directory
   identical  .browserslistrc
The JavaScript app source directory already exists
       apply  /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/webpacker-4.0.7/lib/install/binstubs.rb
  Copying binstubs
       exist    bin
    conflict    bin/webpack
  Overwrite /Volumes/dev/git-dev/rails/sample_app/bin/webpack? (enter "h" for help) [Ynaqdhm] n
        skip    bin/webpack
    conflict    bin/webpack-dev-server
  Overwrite /Volumes/dev/git-dev/rails/sample_app/bin/webpack-dev-server? (enter "h" for help) [Ynaqdhm] n
        skip    bin/webpack-dev-server
File unchanged! Either the supplied flag value not found or the content has already been inserted!  .gitignore
Installing all JavaScript dependencies [4.0.7]
         run  yarn add @rails/webpacker from "."
yarn add v1.22.19
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
success Saved 1 new dependency.
info Direct dependencies
└ @rails/webpacker@5.4.4
info All dependencies
└ @rails/webpacker@5.4.4
✨  Done in 2.44s.
Installing dev server for live reloading
         run  yarn add --dev webpack-dev-server from "."
yarn add v1.22.19
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
success Saved 1 new dependency.
info Direct dependencies
└ webpack-dev-server@4.15.1
info All dependencies
└ webpack-dev-server@4.15.1
✨  Done in 2.15s.
Webpacker successfully installed 🎉 🍰
```

## テストの実行

```bash
$ rails db:migrate
$ rails test
Running via Spring preloader in process 70364
Run options: --seed 54206

# Running:

..

Finished in 2.706464s, 0.7390 runs/s, 0.7390 assertions/s.
2 runs, 2 assertions, 0 failures, 0 errors, 0 skips
```

## About ページのテスト

```ruby
# test/controllers/static_pages_controller_test.rb

  test "should get about" do
    get static_pages_about_url
    assert_response :success
  end
```

```bash
$ rails test
Running via Spring preloader in process 81469
Run options: --seed 20903

# Running:

E

Error:
StaticPagesControllerTest#test_should_get_about:
NameError: undefined local variable or method `static_pages_about_url' for #<StaticPagesControllerTest:0x00007fe4a85fd630>
    test/controllers/static_pages_controller_test.rb:15:in `block in <class:StaticPagesControllerTest>'


rails test test/controllers/static_pages_controller_test.rb:14

..

Finished in 0.832785s, 3.6024 runs/s, 2.4016 assertions/s.
3 runs, 2 assertions, 0 failures, 1 errors, 0 skips
```

## About ページへのルーティング追加

```ruby
# config/routes.rb

  get  'static_pages/about'
```

```bash
$ rails test
Running via Spring preloader in process 94026
Run options: --seed 6122

# Running:

E

Error:
StaticPagesControllerTest#test_should_get_about:
AbstractController::ActionNotFound: The action 'about' could not be found for StaticPagesController
    test/controllers/static_pages_controller_test.rb:15:in `block in <class:StaticPagesControllerTest>'


rails test test/controllers/static_pages_controller_test.rb:14

..

Finished in 0.859043s, 3.4923 runs/s, 2.3282 assertions/s.
3 runs, 2 assertions, 0 failures, 1 errors, 0 skips
```

## About アクションの追加

```ruby
# app/controllers/static_pages_controller.rb

  def about
  end
```

```bash
$ rails test
Running via Spring preloader in process 2127
Run options: --seed 62478

# Running:

E

Error:
StaticPagesControllerTest#test_should_get_about:
ActionController::MissingExactTemplate: StaticPagesController#about is missing a template for request formats: text/html
    test/controllers/static_pages_controller_test.rb:15:in `block in <class:StaticPagesControllerTest>'


rails test test/controllers/static_pages_controller_test.rb:14

..

Finished in 0.856651s, 3.5020 runs/s, 2.3347 assertions/s.
3 runs, 2 assertions, 0 failures, 1 errors, 0 skips
```

## About ビューの追加

```bash
$ touch app/views/static_pages/about.html.erb
```

```ruby
# app/views/static_pages/about.html.erb

<h1>About</h1>
<p>
  <a href="https://railstutorial.jp/">Ruby on Rails Tutorial</a>
  is a <a href="https://railstutorial.jp/#ebook">book</a> and
  <a href="https://railstutorial.jp/screencast">screencast</a>
  to teach web development with
  <a href="https://rubyonrails.org/">Ruby on Rails</a>.
  This is the sample application for the tutorial.
</p>

```

```bash
$ rails test
Running via Spring preloader in process 15608
Run options: --seed 27252

# Running:

...

Finished in 0.903032s, 3.3221 runs/s, 3.3221 assertions/s.
3 runs, 3 assertions, 0 failures, 0 errors, 0 skips
```

## レイアウトファイル名の変更

```bash
$ mv app/views/layouts/application.html.erb layout_file
```

## タイトルテストの追加

```ruby
# test/controllers/static_pages_controller_test.rb

  test "should get home" do
    get static_pages_home_url
    assert_response :success
    assert_select "title", "Home | Ruby on Rails Tutorial Sample App"    
  end

  test "should get help" do
    get static_pages_help_url
    assert_response :success
    assert_select "title", "Help | Ruby on Rails Tutorial Sample App"
  end

  test "should get about" do
    get static_pages_about_url
    assert_response :success
    assert_select "title", "About | Ruby on Rails Tutorial Sample App"
  end
```

```bash
$ rails test
Running via Spring preloader in process 47626
Run options: --seed 25886

# Running:

F

Failure:
StaticPagesControllerTest#test_should_get_help [/Volumes/dev/git-dev/rails/sample_app/test/controllers/static_pages_controller_test.rb:13]:
Expected at least 1 element matching "title", found 0.
Expected 0 to be >= 1.


rails test test/controllers/static_pages_controller_test.rb:10

F

Failure:
StaticPagesControllerTest#test_should_get_home [/Volumes/dev/git-dev/rails/sample_app/test/controllers/static_pages_controller_test.rb:7]:
Expected at least 1 element matching "title", found 0.
Expected 0 to be >= 1.


rails test test/controllers/static_pages_controller_test.rb:4

F

Failure:
StaticPagesControllerTest#test_should_get_about [/Volumes/dev/git-dev/rails/sample_app/test/controllers/static_pages_controller_test.rb:19]:
Expected at least 1 element matching "title", found 0.
Expected 0 to be >= 1.


rails test test/controllers/static_pages_controller_test.rb:16



Finished in 0.112706s, 26.6179 runs/s, 53.2359 assertions/s.
3 runs, 6 assertions, 3 failures, 0 errors, 0 skips
```

## ビューにタイトルを追加

```ruby
# app/views/static_pages/home.html.erb

<!DOCTYPE html>
<html>
  <head>
    <title>Home | Ruby on Rails Tutorial Sample App</title>
  </head>
  <body>
    <h1>Sample App</h1>
    <p>
      This is the home page for the
      <a href="https://railstutorial.jp/">Ruby on Rails Tutorial</a>
      sample application.
    </p>
  </body>
</html>
```

```bash
$ rails test
Running via Spring preloader in process 57541
Run options: --seed 39670

# Running:

...

Finished in 0.089336s, 33.5811 runs/s, 67.1622 assertions/s.
3 runs, 6 assertions, 0 failures, 0 errors, 0 skips
```

## 基本タイトルを使ってテストを記述

```ruby
# test/controllers/static_pages_controller_test.rb

class StaticPagesControllerTest < ActionDispatch::IntegrationTest

  def setup
    @base_title = "Ruby on Rails Tutorial Sample App"
  end

  test "should get home" do
    get static_pages_home_url
    assert_response :success
    assert_select "title", "Home | #{@base_title}"
  end

  test "should get help" do
    get static_pages_help_url
    assert_response :success
    assert_select "title", "Help | #{@base_title}"
  end

  test "should get about" do
    get static_pages_about_url
    assert_response :success
    assert_select "title", "About | #{@base_title}"
  end
end
```

```bash
$ rails test
Running via Spring preloader in process 73760
Run options: --seed 1972

# Running:

...

Finished in 0.105068s, 28.5529 runs/s, 57.1059 assertions/s.
3 runs, 6 assertions, 0 failures, 0 errors, 0 skips
```

## タイトルを provide と yield で表現

```ruby
# app/views/static_pages/home.html.erb

<% provide(:title, "Home") %>
<!DOCTYPE html>
<html>
  <head>
    <title><%= yield(:title) %> | Ruby on Rails Tutorial Sample App</title>
  </head>
```

```bash
$ rails t
Running via Spring preloader in process 29165
Run options: --seed 19653

# Running:

...

Finished in 0.095720s, 31.3414 runs/s, 62.6828 assertions/s.
3 runs, 6 assertions, 0 failures, 0 errors, 0 skips
```

## レイアウトファイル名を元に戻す

```bash
$ mv layout_file app/views/layouts/application.html.erb
```

## レイアウトファイルで yield を定義する

```ruby
# app/views/layouts/application.html.erb

    <title><%= yield(:title) %> | Ruby on Rails Tutorial Sample App</title>
```

## ルーティングの設定

```ruby
# config/routes

Rails.application.routes.draw do
  root 'static_pages#home'
```

## 

##
