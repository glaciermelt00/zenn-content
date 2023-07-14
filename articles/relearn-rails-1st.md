---
title: "Rails の学び直し"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# Ruby 導入

https://railstutorial.jp/chapters/beginning?version=6.0#cha-beginning

```bash
$ rvm get stable
zsh: command not found: rvm
```

## rvm を導入する

参考：　https://rvm.io/

### GPG キーをインストールする

```bash
$ gpg2 --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
zsh: command not found: gpg2
```

### gpg2 をインストールする

参考：　https://stackoverflow.com/questions/54895263/how-to-install-gpg2-via-homebrew

```bash
$ brew install gpg2
...
==> Installing gnupg
==> Pouring gnupg--2.4.3.monterey.bottle.1.tar.gz
🍺  /usr/local/Cellar/gnupg/2.4.3: 140 files, 12.1MB
==> Running `brew cleanup gnupg`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
```

#### 再度、 GPG キーをインストールする

```bash
// gpg2 では認識されない
$ gpg2 --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
zsh: command not found: gpg2

// gnupg でも同様に、認識されない
$ gnupg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
zsh: command not found: gnupg

// gpg で認識された
$ gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
gpg: ディレクトリ'/Users/glaciermelt/.gnupg'が作成されました
gpg: 鍵  105BD0E739499BDB: 1個の重複した署名が除去されました
gpg: /Users/glaciermelt/.gnupg/trustdb.gpg: 信用データベースができました
gpg: 鍵105BD0E739499BDB: 公開鍵"Piotr Kuczynski <piotr.kuczynski@gmail.com>"をインポートしました
gpg: 鍵3804BB82D39DC0E3: 公開鍵"Michal Papis (RVM signing) <mpapis@gmail.com>"をインポートしました
gpg:           処理数の合計: 2
gpg:             インポート: 2
```

### RVM をインストールする

```bash
$ \curl -sSL https://get.rvm.io | bash -s stable
Downloading https://github.com/rvm/rvm/archive/1.29.12.tar.gz
Downloading https://github.com/rvm/rvm/releases/download/1.29.12/1.29.12.tar.gz.asc
gpg: 土  1/16 03:46:22 2021 JSTに施された署名
gpg:                RSA鍵7D2BAF1CF37B13E2069D6956105BD0E739499BDBを使用
gpg: "Piotr Kuczynski <piotr.kuczynski@gmail.com>"からの正しい署名 [不明の]
gpg: *警告*: この鍵は信用できる署名で証明されていません!
gpg:       この署名が所有者のものかどうかの検証手段がありません。
 主鍵フィンガープリント: 7D2B AF1C F37B 13E2 069D  6956 105B D0E7 3949 9BDB
GPG verified '/Users/glaciermelt/.rvm/archives/rvm-1.29.12.tgz'
Installing RVM to /Users/glaciermelt/.rvm/
    Adding rvm PATH line to /Users/glaciermelt/.profile /Users/glaciermelt/.mkshrc /Users/glaciermelt/.bashrc /Users/glaciermelt/.zshrc.
    Adding rvm loading line to /Users/glaciermelt/.profile /Users/glaciermelt/.bash_profile /Users/glaciermelt/.zlogin.
Installation of RVM in /Users/glaciermelt/.rvm/ is almost complete:

  * To start using RVM you need to run `source /Users/glaciermelt/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate
```

#### RVM を起動

```basn
$ source /Users/glaciermelt/.rvm/scripts/rvm
```

## rvm を使用する

### rvm get stable する

```bash
$ rvm get stable
Downloading https://get.rvm.io
Downloading https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer.asc
Verifying /Users/glaciermelt/.rvm/archives/rvm-installer.asc
gpg: 水  2/22 08:35:16 2023 JSTに施された署名
gpg:                RSA鍵7D2BAF1CF37B13E2069D6956105BD0E739499BDBを使用
gpg: "Piotr Kuczynski <piotr.kuczynski@gmail.com>"からの正しい署名 [不明の]
gpg: *警告*: この鍵は信用できる署名で証明されていません!
gpg:       この署名が所有者のものかどうかの検証手段がありません。
 主鍵フィンガープリント: 7D2B AF1C F37B 13E2 069D  6956 105B D0E7 3949 9BDB
GPG verified '/Users/glaciermelt/.rvm/archives/rvm-installer'
Downloading https://github.com/rvm/rvm/archive/1.29.12.tar.gz
Downloading https://github.com/rvm/rvm/releases/download/1.29.12/1.29.12.tar.gz.asc
gpg: 土  1/16 03:46:22 2021 JSTに施された署名
gpg:                RSA鍵7D2BAF1CF37B13E2069D6956105BD0E739499BDBを使用
gpg: "Piotr Kuczynski <piotr.kuczynski@gmail.com>"からの正しい署名 [不明の]
gpg: *警告*: この鍵は信用できる署名で証明されていません!
gpg:       この署名が所有者のものかどうかの検証手段がありません。
 主鍵フィンガープリント: 7D2B AF1C F37B 13E2 069D  6956 105B D0E7 3949 9BDB
GPG verified '/Users/glaciermelt/.rvm/archives/rvm-1.29.12.tgz'
Upgrading the RVM installation in /Users/glaciermelt/.rvm/
    RVM PATH line found in /Users/glaciermelt/.mkshrc /Users/glaciermelt/.profile /Users/glaciermelt/.bashrc /Users/glaciermelt/.zshrc.
    RVM sourcing line found in /Users/glaciermelt/.profile /Users/glaciermelt/.bash_profile /Users/glaciermelt/.zlogin.
Upgrade of RVM in /Users/glaciermelt/.rvm/ is complete.

Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate


RVM reloaded!
```

### rvm install する

```bash
$ rvm install 2.7.6
Searching for binary rubies, this might take some time.
No binary rubies available for: osx/12.6/x86_64/ruby-2.7.6.
Continuing with compilation. Please read 'rvm help mount' to get more information on binary rubies.
Checking requirements for osx.
Installing requirements for osx.
Updating system - please wait
Installing required packages: automake, zlib - please wait
Certificates bundle '/usr/local/etc/openssl@1.1/cert.pem' is already up to date.
Requirements installation successful.
Installing Ruby from source to: /Users/glaciermelt/.rvm/rubies/ruby-2.7.6, this may take a while depending on your cpu(s)...
ruby-2.7.6 - #downloading ruby-2.7.6, this may take a while depending on your connection...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 14.1M  100 14.1M    0     0  12.4M      0  0:00:01  0:00:01 --:--:-- 12.4M
No checksum for downloaded archive, recording checksum in user configuration.
ruby-2.7.6 - #extracting ruby-2.7.6 to /Users/glaciermelt/.rvm/src/ruby-2.7.6 - please wait
ruby-2.7.6 - #configuring - please wait
ruby-2.7.6 - #post-configuration - please wait
ruby-2.7.6 - #compiling - please wait
ruby-2.7.6 - #installing - please wait
Error running '__rvm_make install',
please read /Users/glaciermelt/.rvm/log/1689303579_ruby-2.7.6/install.log
There has been an error while running make install. Halting the installation.
```

ChatGPT を参考に対応する

![](/images/ss_2023-07-14_13_32_34.png)

#### エラーログを確認する

```bash
cat /Users/glaciermelt/.rvm/log/1689303579_ruby-2.7.6/install.log

+__rvm_make:0> make install
./revision.h unchanged
generating x86_64-darwin21-fake.rb
x86_64-darwin21-fake.rb updated
        BASERUBY = /usr/bin/ruby --disable=gems
        CC = gcc
        LD = ld
        LDSHARED = gcc -dynamiclib
        CFLAGS = -g -O2 -fno-common -pipe
        XCFLAGS = -D_FORTIFY_SOURCE=2 -fstack-protector-strong -fno-strict-overflow -fvisibility=hidden -DRUBY_EXPORT -DCANONICALIZATION_FOR_MATHN -I. -I.ext/include/x86_64-darwin21 -I./include -I. -I./enc/unicode/12.1.0
        CPPFLAGS = -I/usr/local/opt/mysql@5.7/include -I/usr/local/opt/libyaml/include -I/usr/local/opt/libksba/include -I/usr/local/opt/readline/include -I/usr/local/opt/zlib/include -I/usr/local/opt/openssl@1.1/include -D_XOPEN_SOURCE -D_DARWIN_C_SOURCE -D_DARWIN_UNLIMITED_SELECT -D_REENTRANT
        DLDFLAGS = -L/usr/local/opt/mysql@5.7/lib -Wl,-undefined,dynamic_lookup -Wl,-multiply_defined,suppress -L/usr/local/opt/libyaml/lib -L/usr/local/opt/libksba/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/zlib/lib -L/usr/local/opt/openssl@1.1/lib -install_name /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/libruby.2.7.dylib -compatibility_version 2.7 -current_version 2.7.6  -fstack-protector-strong -framework Security -framework Foundation  -fstack-protector-strong -framework Security -framework Foundation
        SOLIBS = -lpthread -lgmp -ldl -lobjc
        LANG = ja_JP.UTF-8
        LC_ALL =
        LC_CTYPE =
        MFLAGS =
Apple clang version 14.0.0 (clang-1400.0.29.202)
Target: x86_64-apple-darwin21.6.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
generating enc.mk
making srcs under enc
make[1]: Nothing to be done for `srcs'.
generating transdb.h
transdb.h unchanged
generating makefiles ext/configure-ext.mk
ext/configure-ext.mk updated
generating makefile exts.mk
exts.mk updated
linking shared-object -test-/bug_14834.bundle
ld: warning: -undefined dynamic_lookup may not work with chained fixups
./revision.h unchanged
*** Following extensions are not compiled:
openssl:
        Could not be configured. It will not be installed.
        Check ext/openssl/mkmf.log for more details.
*** Fix the problems, then remove these directories and try again if you want.
making enc
make[1]: Nothing to be done for `enc'.
making trans
make[1]: Nothing to be done for `./enc/trans'.
making encs
make[1]: Nothing to be done for `encs'.
./miniruby -I./lib -I. -I.ext/common  ./tool/runruby.rb --extout=.ext  -- --disable-gems -r./x86_64-darwin21-fake ./tool/rbinstall.rb --make="/Applications/Xcode.app/Contents/Developer/usr/bin/make" --dest-dir="" --extout=".ext" --mflags="" --make-flags="" --data-mode=0644 --prog-mode=0755 --installed-list .installed.list --mantype="doc" --exclude=doc
installing binary commands:         /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/bin
installing base libraries:          /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib
installing arch files:              /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/x86_64-darwin21
installing pkgconfig data:          /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/pkgconfig
installing extension objects:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0/x86_64-darwin21
installing extension objects:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/site_ruby/2.7.0/x86_64-darwin21
installing extension objects:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/vendor_ruby/2.7.0/x86_64-darwin21
installing extension headers:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/include/ruby-2.7.0/x86_64-darwin21
installing extension scripts:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0
installing extension scripts:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/site_ruby/2.7.0
installing extension scripts:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/vendor_ruby/2.7.0
installing extension headers:       /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/include/ruby-2.7.0/ruby
installing command scripts:         /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/bin
installing library scripts:         /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/2.7.0
installing common headers:          /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/include/ruby-2.7.0
installing manpages:                /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/share/man (man1, man5)
installing default gems from lib:   /Users/glaciermelt/.rvm/rubies/ruby-2.7.6/lib/ruby/gems/2.7.0 (build_info, cache, doc, extensions, gems, specifications)
                                    benchmark 0.1.0
/Users/glaciermelt/.rvm/src/ruby-2.7.6/lib/rubygems/core_ext/kernel_require.rb:83:in `require': cannot load such file -- openssl (LoadError)
        from /Users/glaciermelt/.rvm/src/ruby-2.7.6/lib/rubygems/core_ext/kernel_require.rb:83:in `require'
        from /Users/glaciermelt/.rvm/src/ruby-2.7.6/lib/rubygems/specification.rb:2430:in `to_ruby'
        from ./tool/rbinstall.rb:846:in `block (2 levels) in install_default_gem'
        from ./tool/rbinstall.rb:279:in `open_for_install'
        from ./tool/rbinstall.rb:845:in `block in install_default_gem'
        from ./tool/rbinstall.rb:835:in `each'
        from ./tool/rbinstall.rb:835:in `install_default_gem'
        from ./tool/rbinstall.rb:799:in `block in <main>'
        from ./tool/rbinstall.rb:950:in `block in <main>'
        from ./tool/rbinstall.rb:947:in `each'
        from ./tool/rbinstall.rb:947:in `<main>'
make: *** [do-install-nodoc] Error 1
+__rvm_make:0> return 2
```

#### OpenSSL をインストールする

```bash
$ brew install openssl
==> Downloading https://formulae.brew.sh/api/formula.jws.json
######################################################################################################################################################################################################################################################### 100.0%
==> Downloading https://formulae.brew.sh/api/cask.jws.json
######################################################################################################################################################################################################################################################### 100.0%
Warning: openssl@3 3.1.1_1 is already installed and up-to-date.
To reinstall 3.1.1_1, run:
  brew reinstall openssl@3
```

#### インストールされた OpenSSL のパスを取得する

```bash
$ brew --prefix openssl
/usr/local/opt/openssl@3
```

#### OpenSSL のパスを使って、Ruby を再度インストールする

```bash
$ rvm reinstall 2.7.6 --with-openssl-dir=/usr/local/opt/openssl@3
ruby-2.7.6 - #removing src/ruby-2.7.6 - please wait
ruby-2.7.6 - #removing rubies/ruby-2.7.6 - please wait
Checking requirements for osx.
Certificates bundle '/usr/local/etc/openssl@1.1/cert.pem' is already up to date.
Requirements installation successful.
Installing Ruby from source to: /Users/glaciermelt/.rvm/rubies/ruby-2.7.6, this may take a while depending on your cpu(s)...
ruby-2.7.6 - #downloading ruby-2.7.6, this may take a while depending on your connection...
ruby-2.7.6 - #extracting ruby-2.7.6 to /Users/glaciermelt/.rvm/src/ruby-2.7.6 - please wait
ruby-2.7.6 - #configuring - please wait
ruby-2.7.6 - #post-configuration - please wait
ruby-2.7.6 - #compiling - please wait
ruby-2.7.6 - #installing - please wait
Error running '__rvm_make install',
please read /Users/glaciermelt/.rvm/log/1689309399_ruby-2.7.6/install.log
There has been an error while running make install. Halting the installation.
```

#### OpenSSL 1.1 をインストールする

```bash
$ brew install openssl@1.1

==> Downloading https://formulae.brew.sh/api/formula.jws.json
#=#=-  #       #                                                                                                                                                                                                                                               #=O#-     #        #
==> Downloading https://formulae.brew.sh/api/cask.jws.json
#=#=-  #       #                                                                                                                                                                                                                                               #=O#-     #        #                                                                                                                                                                                                                              ######################################################################################################################################################################################################################################################### 100.0%
Warning: openssl@1.1 1.1.1u is already installed and up-to-date.
To reinstall 1.1.1u, run:
  brew reinstall openssl@1.1
```

#### エラー対応

ChatGPT のアドバイスに従って対応する。

![](/images/ss_2023-07-14_13-54-35.png)

##### RVM が管理するディレクトリ内で OpenSSL をいんすtø~るする

```bash
$ rvm pkg install openssl


Beware, 'rvm pkg ...' is deprecated, read about the new autolibs feature: 'rvm help autolibs'.

Checking requirements for osx.
Certificates bundle '/usr/local/etc/openssl@1.1/cert.pem' is already up to date.
Requirements installation successful.
Fetching openssl-1.0.1i.tar.gz to /Users/glaciermelt/.rvm/archives
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 4318k  100 4318k    0     0  4422k      0 --:--:-- --:--:-- --:--:-- 4433k
Extracting openssl to /Users/glaciermelt/.rvm/src/openssl-1.0.1i.....
Configuring openssl in /Users/glaciermelt/.rvm/src/openssl-1.0.1i.......................
Compiling openssl in /Users/glaciermelt/.rvm/src/openssl-1.0.1i.........................................................................................................................................^[[A.^[[B..................................................
Installing openssl to /Users/glaciermelt/.rvm/usr.........................................................................................................................................................

Please note that it's required to reinstall all rubies:

    rvm reinstall all --force

Updating openssl certificates....
```

##### Ruby を再インストールする

```bash
// 2.7.6 を削除
$ rvm remove 2.7.6
ruby-2.7.6 - #removing src/ruby-2.7.6 - please wait
ruby-2.7.6 - #removing rubies/ruby-2.7.6 - please wait
awk: can't open file /Users/glaciermelt/.rvm/config/alias
 source line number 1
Now using system ruby.

// 2.7.6 を再インストール
$ rvm install 2.7.6 --with-openssl-dir=$HOME/.rvm/usr
```

#### GitHub の情報を参考にする

https://github.com/rvm/rvm/issues/5246

```bash
$ PKG_CONFIG_PATH=/usr/local/opt/openssl@1.1/lib/pkgconfig rvm reinstall 2.7.6 --with-openssl-lib=/usr/local/opt/openssl@1.1 --with-openssl-include=/usr/local/include/openssl
ruby-2.7.6 - #removing src/ruby-2.7.6 - please wait
ruby-2.7.6 - #removing rubies/ruby-2.7.6 - please wait
Checking requirements for osx.
Certificates bundle '/usr/local/etc/openssl@1.1/cert.pem' is already up to date.
Requirements installation successful.
Installing Ruby from source to: /Users/glaciermelt/.rvm/rubies/ruby-2.7.6, this may take a while depending on your cpu(s)...
ruby-2.7.6 - #downloading ruby-2.7.6, this may take a while depending on your connection...
ruby-2.7.6 - #extracting ruby-2.7.6 to /Users/glaciermelt/.rvm/src/ruby-2.7.6 - please wait
ruby-2.7.6 - #configuring - please wait
ruby-2.7.6 - #post-configuration - please wait
ruby-2.7.6 - #compiling - please wait
ruby-2.7.6 - #installing - please wait
ruby-2.7.6 - #making binaries executable - please wait
Installed rubygems 3.1.6 is newer than 3.0.9 provided with installed ruby, skipping installation, use --force to force installation.
ruby-2.7.6 - #gemset created /Users/glaciermelt/.rvm/gems/ruby-2.7.6@global
ruby-2.7.6 - #importing gemset /Users/glaciermelt/.rvm/gemsets/global.gems - please wait
ruby-2.7.6 - #generating global wrappers - please wait
ruby-2.7.6 - #gemset created /Users/glaciermelt/.rvm/gems/ruby-2.7.6
ruby-2.7.6 - #importing gemsetfile /Users/glaciermelt/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.7.6 - #generating default wrappers - please wait
ruby-2.7.6 - #adjusting #shebangs for (gem irb erb ri rdoc testrb rake).
Install of ruby-2.7.6 - #complete
Ruby was built without documentation, to build it run: rvm docs generate-ri
Making gemset ruby-2.7.6 pristine - please wait
Making gemset ruby-2.7.6@global pristine - please wait
```

## デフォルトで Ruby 2.7.6 を使う

```bash
$ rvm --default use 2.7.6
Using /Users/glaciermelt/.rvm/gems/ruby-2.7.6
```

## Ruby のバージョンを確認する

```bash
$ ruby -v
ruby 2.7.6p219 (2022-04-12 revision c9c2245c0a) [x86_64-darwin21]
```


# Rails インストール

## Ruby ドキュメントをスキップする

```bash
$ echo "gem: --no-document" >> ~/.gemrc
```

## バージョンを指定して Rails をインストールする

```bash
// gem コマンドで Rails をインストールする
$ gem install rails -v 6.0.4
Fetching concurrent-ruby-1.2.2.gem
Fetching thread_safe-0.3.6.gem
Fetching tzinfo-1.2.11.gem
Fetching rails-dom-testing-2.1.1.gem
Fetching zeitwerk-2.6.8.gem
Fetching nokogiri-1.15.3-x86_64-darwin.gem
Fetching activesupport-6.0.4.gem
Fetching i18n-1.14.1.gem
Fetching crass-1.0.6.gem
Fetching loofah-2.21.3.gem
Fetching rails-html-sanitizer-1.6.0.gem
Fetching erubi-1.12.0.gem
Fetching builder-3.2.4.gem
Fetching actionview-6.0.4.gem
Fetching rack-2.2.7.gem
Fetching rack-test-2.1.0.gem
Fetching actionpack-6.0.4.gem
Fetching sprockets-4.2.0.gem
Fetching sprockets-rails-3.4.2.gem
Fetching method_source-1.0.0.gem
Fetching thor-1.2.2.gem
Fetching railties-6.0.4.gem
Fetching marcel-1.0.2.gem
Fetching activemodel-6.0.4.gem
Fetching activerecord-6.0.4.gem
Fetching globalid-1.1.0.gem
Fetching activejob-6.0.4.gem
Fetching activestorage-6.0.4.gem
Fetching actiontext-6.0.4.gem
Fetching net-protocol-0.2.1.gem
Fetching net-imap-0.3.6.gem
Fetching mini_mime-1.1.2.gem
Fetching mail-2.8.1.gem
Fetching actionmailbox-6.0.4.gem
Fetching websocket-extensions-0.1.5.gem
Fetching websocket-driver-0.7.5.gem
Fetching nio4r-2.5.9.gem
Fetching actioncable-6.0.4.gem
Fetching actionmailer-6.0.4.gem
Fetching rails-6.0.4.gem
Successfully installed zeitwerk-2.6.8
Successfully installed concurrent-ruby-1.2.2
Successfully installed thread_safe-0.3.6
Successfully installed tzinfo-1.2.11
Successfully installed i18n-1.14.1
Successfully installed activesupport-6.0.4
Successfully installed nokogiri-1.15.3-x86_64-darwin
Successfully installed rails-dom-testing-2.1.1
Successfully installed crass-1.0.6
Successfully installed loofah-2.21.3
Successfully installed rails-html-sanitizer-1.6.0
Successfully installed erubi-1.12.0
Successfully installed builder-3.2.4
Successfully installed actionview-6.0.4
Successfully installed rack-2.2.7
Successfully installed rack-test-2.1.0
Successfully installed actionpack-6.0.4
Successfully installed sprockets-4.2.0
Successfully installed sprockets-rails-3.4.2
Successfully installed method_source-1.0.0
Successfully installed thor-1.2.2
Successfully installed railties-6.0.4
Successfully installed marcel-1.0.2
Successfully installed activemodel-6.0.4
Successfully installed activerecord-6.0.4
Successfully installed globalid-1.1.0
Successfully installed activejob-6.0.4
Successfully installed activestorage-6.0.4
Successfully installed actiontext-6.0.4
Successfully installed net-protocol-0.2.1
Successfully installed net-imap-0.3.6
Successfully installed mini_mime-1.1.2
Successfully installed mail-2.8.1
Successfully installed actionmailbox-6.0.4
Successfully installed websocket-extensions-0.1.5
Building native extensions. This could take a while...
Successfully installed websocket-driver-0.7.5
Building native extensions. This could take a while...
Successfully installed nio4r-2.5.9
Successfully installed actioncable-6.0.4
Successfully installed actionmailer-6.0.4
Successfully installed rails-6.0.4
40 gems installed

// rails のバージョンを確認する
$ rails -v
Rails 6.0.4
```

## bundler のバージョンを指定してインストールする

```bash
$ gem install bundler -v 2.2.17
Fetching bundler-2.2.17.gem
Successfully installed bundler-2.2.17
1 gem installed
```

## Yarn のバージョンを確認する

```basn
$ yarn -v
1.22.19
```
