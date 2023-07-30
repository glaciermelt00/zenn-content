---
title: "Rails の学び直し: 9th: 6章 ユーザーのモデルを作成する"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: true
---

ユーザー用のデータモデルを作成していく。

# コラム 6.1 認証システムを作りながら学ぶべき理由

自分で認証システムを構築することで仕組みを理解し、必要に応じて変更することが大切。

# 6.1 User モデル

データベースとやりとりするデフォルトの Rails ライブラリ *Active Record* を使用する。
Active Record は、オブジェクトの作成・保存・検索のためのメソッドを持っている。

Rails には *マイグレーション* 機能がある。

## 6.1.1 データベースの移行

ユーザーオブジェクトについて、 *永続性* という要素が欠けていた。
簡単に消えることのないユーザーのモデルを構築する。

`User` モデルを作成していく。

```bash
$ rails generate model User name:string email:string
Running via Spring preloader in process 65706
      invoke  active_record
      create    db/migrate/20230728235745_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
```

上記により、マイグレ－ションファイルが作成される。

```ruby
# db/migrate/20230728235745_create_users.rb

class CreateUsers < ActiveRecord::Migration[6.0]
  def change
    create_table :users do |t|
      t.string :name
      t.string :email

      t.timestamps
    end
  end
end
```

ブロックの最後の行 `t.timestamps` で、 `created_at` と `updated_at` という 2 つの *マジックカラム* が作成される。

`db:migrate` で *マイグレーションを適用 (migrating up)* する。

```bash
$ rails db:migrate
== 20230728235745 CreateUsers: migrating ======================================
-- create_table(:users)
   -> 0.0025s
== 20230728235745 CreateUsers: migrated (0.0026s) =============================

```

上記で `db/development.sqlite3` ファイルが作成される。
データベースの中身を確認するため、 DB Brower for SQLite をインストールする。

```bash
brew install --cask db-browser-for-sqlite
Running `brew update --auto-update`...
==> Homebrew collects anonymous analytics.
Read the analytics documentation (and how to opt-out) here:
  https://docs.brew.sh/Analytics
No analytics have been recorded yet (nor will be during this `brew` run).

Installing from the API is now the default behaviour!
You can save space and time by running:
  brew untap homebrew/core
  brew untap homebrew/cask
==> Auto-updated Homebrew!
Updated 3 taps (hashicorp/tap, homebrew/services and aws/tap).
Warning: Starting from 2023/8/14, AWS SAM CLI will no longer support installing through aws/tap/aws-sam-cli.
        Please use supported installers, for more information
        https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/install-sam-cli.html

You have 27 outdated formulae and 1 outdated cask installed.

==> Downloading https://github.com/sqlitebrowser/sqlitebrowser/releases/download/v3.12.2/DB.Browser.for.SQLite-3.12.2.dmg
==> Downloading from https://objects.githubusercontent.com/github-production-release-asset-2e65be/19416551/7b84f600-b10b-11eb-8b89-8d2dee117a58?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20230729%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230729T001341Z&X-Amz-Expires=300&X-Amz-Signature=f78336bdc5ab4c81927f89d41d06ce755181c17426132fd7c08add0570d0a70b&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=19416551&response-content-disposition=attachment%3B%20file
######################################################################################################################################################################################################################################################### 100.0%
==> Installing Cask db-browser-for-sqlite
==> Moving App 'DB Browser for SQLite.app' to '/Applications/DB Browser for SQLite.app'
🍺  db-browser-for-sqlite was successfully installed!
```

データベースの中身を確認すると、 `id` というカラムが作成されていることが分かる。

### 演習

#### 1.

`db/schema.db` の中身は下記の通り。

```ruby
# db/schema.db

ActiveRecord::Schema.define(version: 2023_07_28_235745) do

  create_table "users", force: :cascade do |t|
    t.string "name"
    t.string "email"
    t.datetime "created_at", precision: 6, null: false
    t.datetime "updated_at", precision: 6, null: false
  end

end
```

また、マイグレーションファイルの中身は下記の通り。

```ruby
# db/migrate/20230728235745_create_users.rb

class CreateUsers < ActiveRecord::Migration[6.0]
  def change
    create_table :users do |t|
      t.string :name
      t.string :email

      t.timestamps
    end
  end
end
```

`db/schema.db` では `ActiveRecord::Schema` の `define` メソッドに `create_table` ブロックが渡されている。

マイグレーションファイルでは、 `ActiveRecord::Migration` を継承したクラスで `change` メソッドを定義し、その中で `create_table` ブロックを定義している。

#### 2.

`rails db:rollback` で、マイグレーションをロールバックしてみる。

```bash
$ rails db:rollback
== 20230728235745 CreateUsers: reverting ======================================
-- drop_table(:users)
   -> 0.0020s
== 20230728235745 CreateUsers: reverted (0.0048s) =============================
```

ロールバック後、 `db/schema.db` の中身は空となる。

```ruby
# db/schema.db

ActiveRecord::Schema.define(version: 0) do

end
```

ロールバックコマンドにより、 `drop_table` コマンドが呼び出されている。

#### 3.

`rails db:migrate` で、マイグレーションを適用する。

```bash
$ rails db:migrate
== 20230728235745 CreateUsers: migrating ======================================
-- create_table(:users)
   -> 0.0016s
== 20230728235745 CreateUsers: migrated (0.0017s) =============================
```

