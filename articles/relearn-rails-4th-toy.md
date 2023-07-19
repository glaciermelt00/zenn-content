---
title: "Rails の学び直し: 4th"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# Toy アプリケーション

## アプリケーションを作成する

```bash
$ rails _6.0.4_ new toy_app
      create
      create  README.md
.
.
.
Using sass-rails 6.0.0
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
warning @rails/webpacker > node-sass > node-gyp > tar@2.2.2: This version of tar is no longer supported, and will not receive security updates. Please upgrade asap.
warning @rails/webpacker > node-sass > request > har-validator@5.1.5: this library is no longer supported
warning @rails/webpacker > node-sass > request > uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar@2.1.8: Chokidar 2 does not receive security updates since 2019. Upgrade to chokidar 3 with 15x fewer dependencies
warning @rails/webpacker > compression-webpack-plugin > cacache > @npmcli/move-file@1.1.2: This functionality has been moved to @npmcli/fs
warning @rails/webpacker > postcss-preset-env > postcss-color-mod-function > postcss-values-parser > flatten@1.0.3: flatten is deprecated in favor of utility frameworks such as lodash.
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve@0.5.3: See https://github.com/lydell/source-map-resolve#deprecated
warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar > fsevents@1.2.13: The v1 package contains DANGEROUS / INSECURE binaries. Upgrade to safe fsevents v2
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo@1.3.2: This SVGO version is no longer supported. Upgrade to v2.x.x.
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo > stable@0.1.8: Modern JS already guarantees Array#sort() is a stable sort, so this library is deprecated. See the compatibility table on MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#browser_compatibility
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
[1/3] ⠐ fsevents
[2/3] ⠐ core-js
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents
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

[-/3] ⠠ waiting...
[-/3] ⠠ waiting...
error /Volumes/dev/git-dev/rails/toy_app/node_modules/node-sass: Command failed.
Exit code: 1
Command: node scripts/build.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/toy_app/node_modules/node-sass
Output:
Building: /Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node /Volumes/dev/git-dev/rails/toy_app/node_modules/node-gyp/bin/node-gyp.js rebuild --verbose --libsass_ext= --libsass_cflags= --libsass_ldflags= --libsass_library=
gyp info it worked if it ends with ok
gyp verb cli [
gyp verb cli   '/Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node',
gyp verb cli   '/Volumes/dev/git-dev/rails/toy_app/node_modules/node-gyp/bin/node-gyp.js',
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
gyp verb `which` failed     at getNotFoundError (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:13:12)
gyp verb `which` failed     at F (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:68:19)
gyp verb `which` failed     at E (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:80:29)
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:89:16
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/isexe/index.js:42:5
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/isexe/mode.js:8:5
gyp verb `which` failed     at FSReqCallback.oncomplete (node:fs:208:21)
gyp verb `which` failed  python2 Error: not found: python2
gyp verb `which` failed     at getNotFoundError (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:13:12)
gyp verb `which` failed     at F (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:68:19)
gyp verb `which` failed     at E (/Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:80:29)
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/which/which.js:89:16
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/isexe/index.js:42:5
gyp verb `which` failed     at /Volumes/dev/git-dev/rails/toy_app/node_modules/isexe/mode.js:8:5
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
gyp ERR! command "/Users/glaciermelt/.nvm/versions/node/v18.16.0/bin/node" "/Volumes/dev/git-dev/rails/toy_app/node_modules/node-gyp/bin/node-gyp.js" "rebuild" "--verbose" "--libsass_ext=" "--libsass_cflags=" "--libsass_ldflags=" "--libsass_library="
gyp ERR! cwd /Volumes/dev/git-dev/rails/toy_app/node_modules/node-sass
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
.
.
.
└ ws@8.13.0
✨  Done in 11.79s.
Webpacker successfully installed 🎉 🍰
```

## Gemfile を編集

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
  gem 'capybara',           '3.28.0'
  gem 'selenium-webdriver', '3.142.4'
  gem 'webdrivers',         '4.1.2'
end

group :production do
  gem 'pg', '1.1.4'
end

# Windows ではタイムゾーン情報用の tzinfo-data gem を含める必要があります
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

## ローカル gem をインストールする

```bash
// 本番用の gem を除外するよう、 bundle config を設定
$ bundle _2.2.17_ config
Settings are listed in order of priority. The top value will be used.
build.puma
Set for the current user (/Users/glaciermelt/.bundle/config): "--with-cflags=-Wno-error=implicit-function-declaration"

glaciermelt (i386):/Volumes/dev/git-dev/rails/toy_app (main|✚1)$ bundle _2.2.17_ config set --local without 'production'
glaciermelt (i386):/Volumes/dev/git-dev/rails/toy_app (main|✚1)$ bundle _2.2.17_ config
Settings are listed in order of priority. The top value will be used.
build.puma
Set for the current user (/Users/glaciermelt/.bundle/config): "--with-cflags=-Wno-error=implicit-function-declaration"

without
Set for your local app (/Volumes/dev/git-dev/rails/toy_app/.bundle/config): [:production]

// bundle install する
bundle _2.2.17_ install
Fetching gem metadata from https://rubygems.org/...........
You have requested:
  listen = 3.1.5

The bundle currently has listen locked at 3.8.0.
Try running `bundle update listen`

If you are updating multiple gems in your Gemfile at once,
try passing them all to `bundle update`

// エラーが出たので、 bundle update する
$ bundle update
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies.....
Using rake 12.3.3 (was 13.0.6)
.
.
.
Using rails 6.0.4 (was 6.0.6.1)
Bundle updated!
Gems in the group 'production' were not updated.
```

## webpacker をインストールする

```bash
$ rails webpacker:install
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
    conflict  config/webpacker.yml
Overwrite /Volumes/dev/git-dev/rails/toy_app/config/webpacker.yml? (enter "h" for help) [Ynaqdhm] n
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
Overwrite /Volumes/dev/git-dev/rails/toy_app/babel.config.js? (enter "h" for help) [Ynaqdhm] n
        skip  babel.config.js
Copying .browserslistrc to app root directory
   identical  .browserslistrc
The JavaScript app source directory already exists
       apply  /Users/glaciermelt/.rvm/gems/ruby-2.7.6/gems/webpacker-4.0.7/lib/install/binstubs.rb
  Copying binstubs
       exist    bin
    conflict    bin/webpack
  Overwrite /Volumes/dev/git-dev/rails/toy_app/bin/webpack? (enter "h" for help) [Ynaqdhm] n
        skip    bin/webpack
    conflict    bin/webpack-dev-server
  Overwrite /Volumes/dev/git-dev/rails/toy_app/bin/webpack-dev-server? (enter "h" for help) [Ynaqdhm] n
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
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > source-map-url@0.4.1: See https://github.com/lydell/source-map-url#deprecated
warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
warning @rails/webpacker > optimize-css-assets-webpack-plugin > cssnano > cssnano-preset-default > postcss-svgo > svgo > stable@0.1.8: Modern JS already guarantees Array#sort() is a stable sort, so this library is deprecated. See the compatibility table on MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#browser_compatibility
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
[1/2] ⠐ fsevents
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents
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
success Saved 520 new dependencies.
info Direct dependencies
└ @rails/webpacker@5.4.4
info All dependencies
├ @ampproject/remapping@2.2.1
├ @babel/code-frame@7.22.5
├ @babel/compat-data@7.22.9
├ @babel/core@7.22.9
├ @babel/generator@7.22.9
├ @babel/helper-builder-binary-assignment-operator-visitor@7.22.5
├ @babel/helper-replace-supers@7.22.9
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
├─ @babel/plugin-tranorm-modules-systemjs@7.22.5
├ @babel/plugin-transform-modules-umd@7.22.5
├ @babel/plugin-transform-named-capturing-groups-regex@7.22.5
├ @babel/plugin-transform-new-target@7.22.5
├ @babel/plugin-transform-nullish-coalescing-operator@7.22.5
├ @babel/plugin-transform-numeric-separator@7.22.5
├ @babel/plugin-transform-object-rest-spread@7.22.5
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
├─ @babel/plugin-transform-stic-regex@7.22.5
├ @babel/plugin-transform-template-literals@7.22.5
├ @babel/plugin-transform-typeof-symbol@7.22.5
├ @babel/plugin-transform-unicode-escapes@7.22.5
├ @babel/plugin-transform-unicode-property-regex@7.22.5
├ @babel/plugin-transform-unicode-regex@7.22.5
├ @babel/plugin-transform-unicode-sets-regex@7.22.5
├ @babel/preset-env@7.22.9
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
├ array-buffer-byte-length@1.0.0
├ array.prototype.reduce@1.0.5
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
├─ bluebird.7.2
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
├ chrome-trace-event@1.0.3
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
├─ copy-descripto0.1.1
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
├ cssnano-util-same-parent@4.0.1
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
├─ enhanced-relve@4.5.0
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
├ fill-range@4.0.0
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
├─ hash.js@1.7
├ hex-color-regex@1.1.0
├ hmac-drbg@1.0.1
├ hsl-regex@1.0.0
├ hsla-regex@1.0.0
├ https-browserify@1.0.0
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
├ is-array-buffer@3.0.2
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
├ is-shared-array-buffer@1.0.2
├─ is-strg@1.0.7
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
├ lodash@4.17.21
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
  move-concurrently@1.0.1
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
├ parallel-transform@1.2.0
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
├─ posix-character-classes.1.1
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
├─ postcss-initial@3.4.
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
├ postcss-normalize-charset@4.0.1
├ postcss-normalize-display-values@4.0.2
├ postcss-normalize-positions@4.0.2
├ postcss-normalize-repeat-style@4.0.2
├ postcss-normalize-string@4.0.2
├ postcss-normalize-timing-functions@4.0.2
├ postcss-normalize-unicode@4.0.1
├ postcss-normalize-url@4.0.1
├ postcss-normalize-whitespace@4.0.2
├ postcss-ordered-values@4.1.2
├─ postcss-erflow-shorthand@2.0.0
├ postcss-page-break@2.0.0
├ postcss-place@4.0.1
├ postcss-preset-env@6.7.1
.
.
.
└ yocto-queue@0.1.0
✨  Done in 17.69s.
Installing dev server for live reloading
         run  yarn add --dev webpack-dev-server from "."
yarn add v1.22.19
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
[4/4] 🔨  Building fresh packages...
warning Error running install script for optional dependency: "/Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents: Command failed.
Exit code: 1
Command: node install.js
Arguments:
Directory: /Volumes/dev/git-dev/rails/toy_app/node_modules/watchpack-chokidar2/node_modules/fsevents
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
└ webpack-dev-server@4.15.1
info All dependencies
└ webpack-dev-server@4.15.1
✨  Done in 3.04s.
Webpacker successfully installed 🎉 🍰
```

## コントローラにアクションを追加する

```ruby
# app/controllers/application_controller.rb

class ApplicationController < ActionController::Base

  def hello
    render html: "hello, world!"
  end
end
```

## ルートルーティングを設定する

```ruby
# toy_app/config/routes.rb

Rails.application.routes.draw do
  root 'application#hello'
end
```

## Heroku にプッシュする

```bash
// Heroku アプリを作成する
$ heroku create
Creating app... done, ⬢ tranquil-tor-32730
https://tranquil-tor-32730-10dc03d8ffdc.herokuapp.com/ | https://git.heroku.com/tranquil-tor-32730.git

// Heroku のスタックを heroku-20 に設定する
$ heroku stack:set heroku-20
Setting stack to heroku-20... done

// Heroku にプッシュする
$ git push heroku main
Enumerating objects: 118, done.
Counting objects: 100% (118/118), done.
Delta compression using up to 10 threads
Compressing objects: 100% (100/100), done.
Writing objects: 100% (118/118), 160.77 KiB | 8.04 MiB/s, done.
Total 118 (delta 11), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (11/11), done.
remote: Updated 92 paths from 963b083
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
remote: !       Push rejected to tranquil-tor-32730.
remote:
To https://git.heroku.com/tranquil-tor-32730.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://git.heroku.com/tranquil-tor-32730.git'

// ローカルの Gemfile.lock に x86_64-linux を追加する
$ bundle lock --add-platform x86_64-linux
Fetching gem metadata from https://rubygems.org/...........
Resolving dependencies...
Writing lockfile to /Volumes/dev/git-dev/rails/toy_app/Gemfile.lock

// Heroku に再度プッシュする
$ git push heroku main
Enumerating objects: 121, done.
Counting objects: 100% (121/121), done.
Delta compression using up to 10 threads
Compressing objects: 100% (103/103), done.
Writing objects: 100% (121/121), 161.01 KiB | 8.05 MiB/s, done.
Total 121 (delta 13), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (13/13), done.
remote: Updated 92 paths from dcc319a
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
remote:        Installing thread_safe 0.3.6
remote:        Installing minitest 5.18.1
remote:        Fetching builder 3.2.4
remote:        Installing concurrent-ruby 1.2.2
remote:        Installing builder 3.2.4
remote:        Fetching erubi 1.12.0
remote:        Fetching racc 1.7.1
remote:        Fetching crass 1.0.6
remote:        Installing erubi 1.12.0
remote:        Fetching rack 2.2.7
remote:        Installing crass 1.0.6
remote:        Installing racc 1.7.1 with native extensions
remote:        Fetching nio4r 2.5.9
remote:        Installing rack 2.2.7
remote:        Installing nio4r 2.5.9 with native extensions
remote:        Fetching websocket-extensions 0.1.5
remote:        Fetching marcel 1.0.2
remote:        Installing websocket-extensions 0.1.5
remote:        Installing marcel 1.0.2
remote:        Fetching mini_mime 1.1.2
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
remote:        Fetching rack-test 2.1.0
remote:        Installing rack-test 2.1.0
remote:        Fetching rack-proxy 0.7.6
remote:        Installing rack-proxy 0.7.6
remote:        Fetching i18n 1.14.1
remote:        Installing i18n 1.14.1
remote:        Fetching sprockets 3.7.2
remote:        Installing sprockets 3.7.2
remote:        Fetching websocket-driver 0.7.5
remote:        Installing websocket-driver 0.7.5 with native extensions
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
remote:        Installing jbuilder 2.9.1
remote:        Installing activemodel 6.0.4
remote:        Fetching mail 2.8.1
remote:        Fetching rails-html-sanitizer 1.6.0
remote:        Installing rails-html-sanitizer 1.6.0
remote:        Fetching sass-listen 4.0.0
remote:        Installing mail 2.8.1
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
remote:        Fetching actioncable 6.0.4
remote:        Fetching activestorage 6.0.4
remote:        Installing actioncable 6.0.4
remote:        Installing activestorage 6.0.4
remote:        Fetching actionmailer 6.0.4
remote:        Fetching railties 6.0.4
remote:        Installing railties 6.0.4
remote:        Installing actionmailer 6.0.4
remote:        Fetching sprockets-rails 3.4.2
remote:        Installing sprockets-rails 3.4.2
remote:        Fetching actionmailbox 6.0.4
remote:        Installing actionmailbox 6.0.4
remote:        Fetching actiontext 6.0.4
remote:        Fetching sass-rails 5.1.0
remote:        Installing sass-rails 5.1.0
remote:        Fetching webpacker 4.0.7
remote:        Installing actiontext 6.0.4
remote:        Installing webpacker 4.0.7
remote:        Fetching rails 6.0.4
remote:        Installing rails 6.0.4
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
remote:        Bundle completed (28.70s)
remote:        Cleaning up the bundler cache.
remote: -----> Installing node-v16.18.1-linux-x64
remote: -----> Installing yarn-v1.22.19
remote: -----> Detecting rake tasks
remote: -----> Preparing app for Rails asset pipeline
remote:        Running: rake assets:precompile
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
remote:        yarn install v1.22.19
remote:        [1/4] Resolving packages...
remote:        [2/4] Fetching packages...
remote:        [3/4] Linking dependencies...
remote:        warning "webpack-dev-server > webpack-dev-middleware@5.3.3" has unmet peer dependency "webpack@^4.0.0 || ^5.0.0".
remote:        [4/4] Building fresh packages...
remote:        Done in 13.71s.
remote:        I, [2023-07-16T00:58:34.328099 #1086]  INFO -- : Writing /tmp/build_a6357ff5/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css
remote:        I, [2023-07-16T00:58:34.328531 #1086]  INFO -- : Writing /tmp/build_a6357ff5/public/assets/application-e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855.css.gz
remote:        Compiling
remote:        Compiled all packs in /tmp/build_a6357ff5/public/packs
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
remote:        Time: 3329ms
remote:        Built at: 07/16/2023 12:58:39 AM
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
remote:        Asset precompilation completed (20.70s)
remote:        Cleaning assets
remote:        Running: rake assets:clean
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
remote:        /tmp/build_a6357ff5/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
remote:        /tmp/build_a6357ff5/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
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
remote:        Done: 79.1M
remote: -----> Launching...
remote:  !     The following add-ons were automatically provisioned: heroku-postgresql. These add-ons may incur additional cost, which is prorated to the second. Run `heroku addons` for more info.
remote:        Released v7
remote:        https://tranquil-tor-32730-10dc03d8ffdc.herokuapp.com/ deployed to Heroku
remote:
remote: This app is using the Heroku-20 stack, however a newer stack is available.
remote: To upgrade to Heroku-22, see:
remote: https://devcenter.heroku.com/articles/upgrading-to-the-latest-stack
remote:
remote: Verifying deploy... done.
To https://git.heroku.com/tranquil-tor-32730.git
 * [new branch]      main -> main
```

## ログを調べる

```bash
$ heroku logs --tail --app tranquil-tor-32730
2023-07-16T00:58:57.733680+00:00 app[web.1]: => Run `rails server --help` for more startup options
2023-07-16T00:58:58.551631+00:00 app[web.1]: Puma starting in single mode...
2023-07-16T00:58:58.551649+00:00 app[web.1]: * Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
2023-07-16T00:58:58.551651+00:00 app[web.1]: * Min threads: 5, max threads: 5
2023-07-16T00:58:58.551651+00:00 app[web.1]: * Environment: production
2023-07-16T00:58:58.551927+00:00 app[web.1]: * Listening on tcp://0.0.0.0:16441
2023-07-16T00:58:58.552095+00:00 app[web.1]: Use Ctrl-C to stop
2023-07-16T00:58:59.033096+00:00 heroku[web.1]: State changed from starting to up
2023-07-17T01:07:08.240966+00:00 heroku[web.1]: Cycling
2023-07-17T01:07:08.243343+00:00 heroku[web.1]: State changed from up to starting
2023-07-17T01:07:08.929743+00:00 heroku[web.1]: Stopping all processes with SIGTERM
2023-07-17T01:07:08.965260+00:00 app[web.1]: - Gracefully stopping, waiting for requests to finish
2023-07-17T01:07:08.974834+00:00 app[web.1]: === puma shutdown: 2023-07-17 01:07:08 +0000 ===
2023-07-17T01:07:08.974836+00:00 app[web.1]: - Goodbye!
2023-07-17T01:07:08.976243+00:00 app[web.1]: Exiting
2023-07-17T01:07:09.195056+00:00 heroku[web.1]: Process exited with status 143
2023-07-17T01:07:13.396989+00:00 heroku[web.1]: Starting process with command `bin/rails server -p ${PORT:-5000} -e production`
2023-07-17T01:07:15.812548+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
2023-07-17T01:07:15.812579+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
2023-07-17T01:07:15.812579+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
2023-07-17T01:07:15.812579+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
2023-07-17T01:07:15.812579+00:00 app[web.1]: /app/vendor/ruby-2.7.6/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
2023-07-17T01:07:15.812580+00:00 app[web.1]: /app/vendor/bundle/ruby/2.7.0/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
2023-07-17T01:07:15.861768+00:00 app[web.1]: => Booting Puma
2023-07-17T01:07:15.861770+00:00 app[web.1]: => Rails 6.0.4 application starting in production
2023-07-17T01:07:15.861770+00:00 app[web.1]: => Run `rails server --help` for more startup options
2023-07-17T01:07:16.612937+00:00 app[web.1]: Puma starting in single mode...
2023-07-17T01:07:16.612958+00:00 app[web.1]: * Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
2023-07-17T01:07:16.612959+00:00 app[web.1]: * Min threads: 5, max threads: 5
2023-07-17T01:07:16.612959+00:00 app[web.1]: * Environment: production
2023-07-17T01:07:16.613161+00:00 app[web.1]: * Listening on tcp://0.0.0.0:55746
2023-07-17T01:07:16.613331+00:00 app[web.1]: Use Ctrl-C to stop
2023-07-17T01:07:16.835141+00:00 heroku[web.1]: State changed from starting to up
2023-07-17T04:19:08.000000+00:00 app[api]: Build started by user glacier-melt@hotmail.co.jp
2023-07-17T04:19:49.534023+00:00 app[api]: Release v8 created by user glacier-melt@hotmail.co.jp
2023-07-17T04:19:49.534023+00:00 app[api]: Deploy 2fe73a58 by user glacier-melt@hotmail.co.jp
2023-07-17T04:19:49.738381+00:00 heroku[web.1]: Restarting
2023-07-17T04:19:49.740561+00:00 heroku[web.1]: State changed from up to starting
2023-07-17T04:19:50.364070+00:00 heroku[web.1]: Stopping all processes with SIGTERM
2023-07-17T04:19:50.402041+00:00 app[web.1]: - Gracefully stopping, waiting for requests to finish
2023-07-17T04:19:50.403479+00:00 app[web.1]: === puma shutdown: 2023-07-17 04:19:50 +0000 ===
2023-07-17T04:19:50.403482+00:00 app[web.1]: - Goodbye!
2023-07-17T04:19:50.404883+00:00 app[web.1]: Exiting
2023-07-17T04:19:50.587132+00:00 heroku[web.1]: Process exited with status 143
2023-07-17T04:19:52.000000+00:00 app[api]: Build succeeded
2023-07-17T04:19:53.617622+00:00 heroku[web.1]: Starting process with command `bin/rails server -p ${PORT:-5000} -e production`
2023-07-17T04:19:55.835394+00:00 app[web.1]: => Booting Puma
2023-07-17T04:19:55.835406+00:00 app[web.1]: => Rails 6.0.4 application starting in production
2023-07-17T04:19:55.835407+00:00 app[web.1]: => Run `rails server --help` for more startup options
2023-07-17T04:19:56.517135+00:00 app[web.1]: Puma starting in single mode...
2023-07-17T04:19:56.517161+00:00 app[web.1]: * Version 4.3.6 (ruby 2.7.6-p219), codename: Mysterious Traveller
2023-07-17T04:19:56.517162+00:00 app[web.1]: * Min threads: 5, max threads: 5
2023-07-17T04:19:56.517162+00:00 app[web.1]: * Environment: production
2023-07-17T04:19:56.517316+00:00 app[web.1]: * Listening on tcp://0.0.0.0:54525
2023-07-17T04:19:56.517477+00:00 app[web.1]: Use Ctrl-C to stop
2023-07-17T04:19:56.883199+00:00 heroku[web.1]: State changed from starting to up
2023-07-17T04:20:44.263577+00:00 app[web.1]: I, [2023-07-17T04:20:44.263473 #2]  INFO -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4] Started GET "/" for 217.178.26.43 at 2023-07-17 04:20:44 +0000
2023-07-17T04:20:44.265279+00:00 app[web.1]: I, [2023-07-17T04:20:44.265207 #2]  INFO -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4] Processing by UsersController#index as HTML
2023-07-17T04:20:44.271230+00:00 app[web.1]: I, [2023-07-17T04:20:44.271167 #2]  INFO -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4]   Rendering users/index.html.erb within layouts/application
2023-07-17T04:20:44.400492+00:00 app[web.1]: D, [2023-07-17T04:20:44.400412 #2] DEBUG -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4]   User Load (1.3ms)  SELECT "users".* FROM "users"
2023-07-17T04:20:44.400549+00:00 app[web.1]: I, [2023-07-17T04:20:44.400527 #2]  INFO -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4]   Rendered users/index.html.erb within layouts/application (Duration: 129.3ms | Allocations: 4797)
2023-07-17T04:20:44.400680+00:00 app[web.1]: I, [2023-07-17T04:20:44.400662 #2]  INFO -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4] Completed 500 Internal Server Error in 135ms (ActiveRecord: 71.8ms | Allocations: 6254)
2023-07-17T04:20:44.401472+00:00 app[web.1]: F, [2023-07-17T04:20:44.401443 #2] FATAL -- : [373a3e2b-9460-42d7-9f1d-f16660d010f4]
2023-07-17T04:20:44.401473+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4] ActionView::Template::Error (PG::UndefinedTable: ERROR:  relation "users" does not exist
2023-07-17T04:20:44.401473+00:00 app[web.1]: LINE 1: SELECT "users".* FROM "users"
2023-07-17T04:20:44.401474+00:00 app[web.1]: ^
2023-07-17T04:20:44.401474+00:00 app[web.1]: ):
2023-07-17T04:20:44.401475+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     12:   </thead>
2023-07-17T04:20:44.401476+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     13:
2023-07-17T04:20:44.401476+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     14:   <tbody>
2023-07-17T04:20:44.401477+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     15:     <% @users.each do |user| %>
2023-07-17T04:20:44.401477+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     16:       <tr>
2023-07-17T04:20:44.401478+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     17:         <td><%= user.name %></td>
2023-07-17T04:20:44.401478+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]     18:         <td><%= user.email %></td>
2023-07-17T04:20:44.401478+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4]
2023-07-17T04:20:44.401478+00:00 app[web.1]: [373a3e2b-9460-42d7-9f1d-f16660d010f4] app/views/users/index.html.erb:15
2023-07-17T04:20:44.401601+00:00 heroku[router]: at=info method=GET path="/" host=tranquil-tor-32730-10dc03d8ffdc.herokuapp.com request_id=373a3e2b-9460-42d7-9f1d-f16660d010f4 fwd="217.178.26.43" dyno=web.1 connect=0ms service=142ms status=500 bytes=1827 protocol=https
2023-07-17T04:20:44.681033+00:00 heroku[router]: at=info method=GET path="/favicon.ico" host=tranquil-tor-32730-10dc03d8ffdc.herokuapp.com request_id=ce75d54a-8bf1-47c1-bc18-d9090a648dff fwd="217.178.26.43" dyno=web.1 connect=0ms service=4ms status=200 bytes=143 protocol=https
2023-07-17T04:22:05.009167+00:00 app[web.1]: I, [2023-07-17T04:22:05.009110 #2]  INFO -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0] Started GET "/" for 217.178.26.43 at 2023-07-17 04:22:05 +0000
2023-07-17T04:22:05.009747+00:00 app[web.1]: I, [2023-07-17T04:22:05.009718 #2]  INFO -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0] Processing by UsersController#index as HTML
2023-07-17T04:22:05.010478+00:00 app[web.1]: I, [2023-07-17T04:22:05.010448 #2]  INFO -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0]   Rendering users/index.html.erb within layouts/application
2023-07-17T04:22:05.012757+00:00 app[web.1]: D, [2023-07-17T04:22:05.012723 #2] DEBUG -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0]   User Load (1.0ms)  SELECT "users".* FROM "users"
2023-07-17T04:22:05.012833+00:00 app[web.1]: I, [2023-07-17T04:22:05.012813 #2]  INFO -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0]   Rendered users/index.html.erb within layouts/application (Duration: 2.3ms | Allocations: 257)
2023-07-17T04:22:05.012943+00:00 app[web.1]: I, [2023-07-17T04:22:05.012909 #2]  INFO -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0] Completed 500 Internal Server Error in 3ms (ActiveRecord: 1.0ms | Allocations: 588)
2023-07-17T04:22:05.013707+00:00 app[web.1]: F, [2023-07-17T04:22:05.013684 #2] FATAL -- : [739cf73c-196e-4f59-ae50-2eb55a737fd0]
2023-07-17T04:22:05.013709+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0] ActionView::Template::Error (PG::UndefinedTable: ERROR:  relation "users" does not exist
2023-07-17T04:22:05.013709+00:00 app[web.1]: LINE 1: SELECT "users".* FROM "users"
2023-07-17T04:22:05.013709+00:00 app[web.1]: ^
2023-07-17T04:22:05.013710+00:00 app[web.1]: ):
2023-07-17T04:22:05.013711+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     12:   </thead>
2023-07-17T04:22:05.013711+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     13:
2023-07-17T04:22:05.013712+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     14:   <tbody>
2023-07-17T04:22:05.013712+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     15:     <% @users.each do |user| %>
2023-07-17T04:22:05.013712+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     16:       <tr>
2023-07-17T04:22:05.013713+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     17:         <td><%= user.name %></td>
2023-07-17T04:22:05.013713+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]     18:         <td><%= user.email %></td>
2023-07-17T04:22:05.013713+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0]
2023-07-17T04:22:05.013714+00:00 app[web.1]: [739cf73c-196e-4f59-ae50-2eb55a737fd0] app/views/users/index.html.erb:15
2023-07-17T04:22:05.013873+00:00 heroku[router]: at=info method=GET path="/" host=tranquil-tor-32730-10dc03d8ffdc.herokuapp.com request_id=739cf73c-196e-4f59-ae50-2eb55a737fd0 fwd="217.178.26.43" dyno=web.1 connect=0ms service=6ms status=500 bytes=1827 protocol=https
2023-07-17T04:22:05.294657+00:00 heroku[router]: at=info method=GET path="/favicon.ico" host=tranquil-tor-32730-10dc03d8ffdc.herokuapp.com request_id=9c550059-689c-46a6-9551-a0f554992cff fwd="217.178.26.43" dyno=web.1 connect=0ms service=1ms status=304 bytes=48 protocol=https
```

## データベースマイグレーションを実行する

```bash
$ heroku run rails db:migrate
Running rails db:migrate on ⬢ tranquil-tor-32730... up, run.3731 (Basic)
D, [2023-07-17T04:28:29.080269 #2] DEBUG -- :    (33.5ms)  CREATE TABLE "schema_migrations" ("version" character varying NOT NULL PRIMARY KEY)
D, [2023-07-17T04:28:29.087498 #2] DEBUG -- :    (5.5ms)  CREATE TABLE "ar_internal_metadata" ("key" character varying NOT NULL PRIMARY KEY, "value" character varying, "created_at" timestamp(6) NOT NULL, "updated_at" timestamp(6) NOT NULL)
D, [2023-07-17T04:28:29.122903 #2] DEBUG -- :    (0.6ms)  SELECT pg_try_advisory_lock(1337448099391924485)
D, [2023-07-17T04:28:29.144716 #2] DEBUG -- :    (0.9ms)  SELECT "schema_migrations"."version" FROM "schema_migrations" ORDER BY "schema_migrations"."version" ASC
I, [2023-07-17T04:28:29.145565 #2]  INFO -- : Migrating to CreateUsers (20230716103741)
== 20230716103741 CreateUsers: migrating ======================================
-- create_table(:users)
D, [2023-07-17T04:28:29.148107 #2] DEBUG -- :    (0.6ms)  BEGIN
D, [2023-07-17T04:28:29.156678 #2] DEBUG -- :    (8.5ms)  CREATE TABLE "users" ("id" bigserial primary key, "name" character varying, "email" character varying, "created_at" timestamp(6) NOT NULL, "updated_at" timestamp(6) NOT NULL)
   -> 0.0095s
== 20230716103741 CreateUsers: migrated (0.0096s) =============================

D, [2023-07-17T04:28:29.159701 #2] DEBUG -- :   ActiveRecord::SchemaMigration Create (0.7ms)  INSERT INTO "schema_migrations" ("version") VALUES ($1) RETURNING "version"  [["version", "20230716103741"]]
D, [2023-07-17T04:28:29.161395 #2] DEBUG -- :    (1.6ms)  COMMIT
I, [2023-07-17T04:28:29.161438 #2]  INFO -- : Migrating to CreateMicroposts (20230717013928)
== 20230717013928 CreateMicroposts: migrating =================================
-- create_table(:microposts)
D, [2023-07-17T04:28:29.162544 #2] DEBUG -- :    (0.5ms)  BEGIN
D, [2023-07-17T04:28:29.168111 #2] DEBUG -- :    (5.5ms)  CREATE TABLE "microposts" ("id" bigserial primary key, "content" text, "user_id" integer, "created_at" timestamp(6) NOT NULL, "updated_at" timestamp(6) NOT NULL)
   -> 0.0064s
== 20230717013928 CreateMicroposts: migrated (0.0064s) ========================

D, [2023-07-17T04:28:29.169080 #2] DEBUG -- :   ActiveRecord::SchemaMigration Create (0.6ms)  INSERT INTO "schema_migrations" ("version") VALUES ($1) RETURNING "version"  [["version", "20230717013928"]]
D, [2023-07-17T04:28:29.170484 #2] DEBUG -- :    (1.3ms)  COMMIT
D, [2023-07-17T04:28:29.175458 #2] DEBUG -- :   ActiveRecord::InternalMetadata Load (0.7ms)  SELECT "ar_internal_metadata".* FROM "ar_internal_metadata" WHERE "ar_internal_metadata"."key" = $1 LIMIT $2  [["key", "environment"], ["LIMIT", 1]]
D, [2023-07-17T04:28:29.180291 #2] DEBUG -- :    (0.8ms)  BEGIN
D, [2023-07-17T04:28:29.182310 #2] DEBUG -- :   ActiveRecord::InternalMetadata Create (1.4ms)  INSERT INTO "ar_internal_metadata" ("key", "value", "created_at", "updated_at") VALUES ($1, $2, $3, $4) RETURNING "key"  [["key", "environment"], ["value", "production"], ["created_at", "2023-07-17 04:28:29.179158"], ["updated_at", "2023-07-17 04:28:29.179158"]]
D, [2023-07-17T04:28:29.183568 #2] DEBUG -- :    (1.1ms)  COMMIT
D, [2023-07-17T04:28:29.184410 #2] DEBUG -- :    (0.7ms)  SELECT pg_advisory_unlock(1337448099391924485)
```

##
