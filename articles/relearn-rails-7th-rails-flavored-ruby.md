---
title: "Rails の学び直し: 7th: Rails 風味の Ruby"
emoji: "🧐"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["rails"]
published: false
---

# Rails 風味の Ruby

## full_title ヘルパーを定義する

```ruby
# app/helpers/application_helper.rb

module ApplicationHelper

  # ページごとの完全なタイトルを返します。
  def full_title(page_title = '')
    base_title = "Ruby on Rails Tutorial Sample App"
    if page_title.empty?
      base_title
    else
      page_title + " | " + base_title
    end
  end
end
```

## レイアウトビューでヘルパー関数を使う

```ruby
# app/views/layouts/application.html.erb

    <title><%= full_title(yield(:title)) %></title>
```

## テストを追加する

```ruby
# test/controllers/static_pages_controller_test.rb

  test "should get root" do
    get root_url
    assert_response :success
    assert_select "title", "#{@base_title}}"
  end
```

```bash
$ rails t
Running via Spring preloader in process 14364
Started with run options --seed 40313

 FAIL["test_should_get_root", #<Minitest::Reporters::Suite:0x00007f87f2c3b2f8 @name="StaticPagesControllerTest">, 0.9880210000555962]
 test_should_get_root#StaticPagesControllerTest (0.99s)
        --- expected
        +++ actual
        @@ -1 +1 @@
        -"Ruby on Rails Tutorial Sample App}"
        +"Home | Ruby on Rails Tutorial Sample App"
        .
        Expected 0 to be >= 1.
        test/controllers/static_pages_controller_test.rb:12:in `block in <class:StaticPagesControllerTest>'

  5/5: [====================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:00, Time: 00:00:00

Finished in 1.03739s
5 tests, 10 assertions, 1 failures, 0 errors, 0 skips
```

## ビューを変更

```ruby
# app/views/static_pages/home.html.erb

<h1>Sample App</h1>
<p>
  This is the home page for the
  <a href="https://railstutorial.jp/">Ruby on Rails Tutorial</a>
  sample application.
</p>
```

```bash
21:32:49 - INFO - Running: test/controllers/static_pages_controller_test.rb
Running via Spring preloader in process 45392
Started with run options --seed 40168

  4/4: [====================================================================================================================================================================================================================================================================================================================================================================================================================================================================] 100% Time: 00:00:01, Time: 00:00:01

Finished in 1.05798s
4 tests, 8 assertions, 0 failures, 0 errors, 0 skips
```

## .irbrc の設定

```ruby
# ~/.irbrc

IRB.conf[:PROMPT_MODE] = :SIMPLE
IRB.conf[:AUTO_INDENT_MODE] = false
```

## Rails コンソール

```bash
$ rails console
Running via Spring preloader in process 9544
Loading development environment (Rails 6.0.4)
>>
```

## コメント

```bash
>> 17 + 42 # コメント
=> 59
>>
```

## 文字列

```bash
>> "" # 空の文字列
=> ""
>> "foo" # 空でない文字列
=> "foo"

>> "foo" + "bar"    # 文字列の結合
=> "foobar"

>> first_name = "Michael"    # 変数の代入
=> "Michael"
>> "#{first_name} Hartl"     # 文字列の式展開
=> "Michael Hartl"

>> puts "foo"     # 文字列を出力する
foo
=> nil

>> print "foo\n"  # puts "foo" と等価
foo
=> nil

>> 'foo'          # シングルクォートの文字列
=> "foo"
>> 'foo' + 'bar'
=> "foobar"

>> '#{foo} bar'     # シングルクォート内の文字列では式展開ができない
=> "\#{foo} bar"

>> '\n'       # 'バックスラッシュ n' をそのまま扱う
=> "\\n"

>> 'Newlines (\n) and tabs (\t) both use the backslash character \.'
=> "Newlines (\\n) and tabs (\\t) both use the backslash character \\."
```

## オブジェクトとメッセージ受け渡し

```bash
>> "foobar".length        # 文字列に "length" というメッセージを送る
=> 6

>> "foobar".empty?
=> false
>> "".empty?
=> true

>> s = "foobar"
=> "foobar"
?> if s.empty?
?>   "The string is empty"
?> else
?>   "The string is nonempty"
>> end
=> "The string is nonempty"

?> if s.nil?
?>   "The variable is nil"
?> elsif s.empty?
?>   "The string is empty"
?>   elsif s.include?("foo")
?>     "The string includes 'foo'"
>> end
=> "The string includes 'foo'"

>> nil.to_s
=> ""

>> nil.empty?
Traceback (most recent call last):
        1: from (irb):43
NoMethodError (undefined method 'empty?' for nil:NilClass)
>> nil.to_s.empty?      # メソッドチェーンの例
=> true

>> string = "foobar"
=> "foobar"
>> puts "The string '#{string}' is nonempty." unless string.empty?
The string 'foobar' is nonempty.
=> nil

>> !!nil
=> false

>> !!0
=> true
```

## メソッドの定義

```bash
?> def string_message(str = '')
?>   if str.empty?
?>     "It's an empty string!"
?>   else
?>     "The string is nonempty."
?>   end
>> end
=> :string_message
>> puts string_message("foobar")
The string is nonempty.
=> nil
>> puts string_message("")
It's an empty string!
=> nil
>> puts string_message
It's an empty string!
=> nil

// 関数を定義してみる
?> def string_message(the_function_argument = '')
?>   if the_function_argument.empty?
?>     "It's an empty string!"
?>   else
?>     "The string is nonempty."
?>   end
>> end
=> :string_message
>> puts string_message("")
It's an empty string!
=> nil
>> puts string_message("foobar")
The string is nonempty.
=> nil

// 回文を判定する関数を定義してみる
?> def palindrome_tester(s)
?>   if s == s.reverse
?>     puts "It's a palindrome!"
?>   else
?>     puts "It's not a palindrome."
?>   end
>> end
=> :palindrome_tester
>> palindrome_tester("racecar")
It's a palindrome!
=> nil
>> palindrome_tester("onomatopoeia")
It's not a palindrome.
=> nil
>> palindrome_tester("racecar").nil?
It's a palindrome!
=> true
```

## 配列と範囲演算子

```bash
>> "foo bar     baz".split     # 文字列を3つの要素を持つ配列に分割する
=> ["foo", "bar", "baz"]

>> "fooxbarxbaz".split('x')
=> ["foo", "bar", "baz"]

>> a = [42, 8, 17]
=> [42, 8, 17]
>> a[0]
=> 42
>> a[1]
=> 8
>> a[2]
=> 17
>> a[-1]
=> 17

>> a                  # 配列「a」の内容を確認する
=> [42, 8, 17]
>> a.first
=> 42
>> a.second
=> 8
>> a.last
=> 17
>> a.last == a[-1]    # == を使って比較する
=> true

>> x = a.length       # 配列も文字列と同様lengthメソッドに応答する
=> 3
>> x == 3
=> true
>> x == 1
=> false
>> x != 1
=> true
>> x >= 1
=> true
>> x < 1
=> false

>> a
=> [42, 8, 17]
>> a.empty?
=> false
>> a.includes?(42)
Traceback (most recent call last):
        1: from (irb):22
NoMethodError (undefined method 'includes?' for [42, 8, 17]:Array)
Did you mean?  include?
               including
>> a.include?(42)
=> true
>> a.sort
=> [8, 17, 42]
>> a
=> [42, 8, 17]
>> a.reverse
=> [17, 8, 42]
>> a.shuffle
=> [8, 17, 42]
>> a
=> [42, 8, 17]

>> a
=> [42, 8, 17]
>> a.sort!
=> [8, 17, 42]
>> a
=> [8, 17, 42]

>> a.push(6)                  # 6を配列に追加する
=> [8, 17, 42, 6]
>> a << 7                     # 7を配列に追加する
=> [8, 17, 42, 6, 7]
>> a << "foo" << "bar"        # 配列に連続して追加する
=> [8, 17, 42, 6, 7, "foo", "bar"]

>> a
=> [8, 17, 42, 6, 7, "foo", "bar"]
>> a.join                       # 単純に連結する
=> "8174267foobar"
>> a.join(', ')                 # カンマ+スペースを使って連結する
=> "8, 17, 42, 6, 7, foo, bar"

>> 0..9
=> 0..9
>> 0..9.to_a              # おっと、9に対してto_aを呼んでしまっていますね
Traceback (most recent call last):
        1: from (irb):39
NoMethodError (undefined method 'to_a' for 9:Integer)
Did you mean?  to_s
               to_d
               to_c
               to_r
               to_f
               to_i
>> (0..9).to_a            # 丸カッコを使い、範囲オブジェクトに対してto_aを呼びましょう
=> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>> a = %w[foo bar baz quux]         # %wを使って文字列の配列に変換
=> ["foo", "bar", "baz", "quux"]
>> a[0..2]
=> ["foo", "bar", "baz"]

>> a = (0..9).to_a
=> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>> a[2..(a.length-1)]               # 明示的に配列の長さを使って選択
=> [2, 3, 4, 5, 6, 7, 8, 9]
>> a[2..-1]                         # 添字に-1を使って選択
=> [2, 3, 4, 5, 6, 7, 8, 9]

>> ('a'..'e').to_a
=> ["a", "b", "c", "d", "e"]

// 演習
>> a = "A man, a plan, a canal, Panama".split(',')
=> ["A man", " a plan", " a canal", " Panama"]

>> s = a.join
=> "A man a plan a canal Panama"

>> s.split(' ').join
=> "AmanaplanacanalPanama"

?> def palindrome_tester(s)
?>   if s == s.reverse
?>     puts "It's a palindrome!"
?>   else
?>     puts "It's not a palindrome."
?>   end
>> end
=> :palindrome_tester
>> palindrome_tester(s.sp.it(' ').join)
Traceback (most recent call last):
        1: from (irb):57
NoMethodError (undefined method `sp' for "A man a plan a canal Panama":String)
>> palindrome_tester(s.split(' ').join)
It's not a palindrome.
=> nil
>> palindrome_tester(s.downcase.split(' ').join)
It's a palindrome!
=> nil

>> ('a'..'z')
=> "a".."z"
>> ('a'..'z')[0]
Traceback (most recent call last):
        1: from (irb):61
NoMethodError (undefined method `[]' for "a".."z":Range)
>> ('a'..'z').to_a[0]
=> "a"
>> ('a'..'z').to_a[-7]
=> "t"
```

## ブロック

```bash
>> (1..5).each { |i| puts 2 * i }
2
4
6
8
10
=> 1..5
?> (1..5).each do |i|
?>   puts 2 * i
>> end
2
4
6
8
10
=> 1..5

?> (1..5).each do |number|
?>   puts 2 * number
?>   puts '--'
>> end
2
--
4
--
6
--
8
--
10
--
=> 1..5

>> 3.times { puts "Betelgeuse!" }   # 3.timesではブロックに変数を使っていない
Betelgeuse!
Betelgeuse!
Betelgeuse!
=> 3

>> (1..5).map { |i| i**2 }          # 「**」記法は冪乗 (べき乗)
=> [1, 4, 9, 16, 25]

>> %w[a b c]                        # %w で文字列の配列を作成
=> ["a", "b", "c"]
>> %w[a b c].map { |char| char.upcase }
=> ["A", "B", "C"]
>> %w[A B C].map { |char| char.downcase }
=> ["a", "b", "c"]

>>  %w[A B C].map { |char| char.downcase }
=> ["a", "b", "c"]
>> %w[A B C].map(&:downcase)
=> ["a", "b", "c"]

>> ('a'..'z').to_a                     # 英小文字を列挙した配列を作る
=> ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]
>> ('a'..'z').to_a.shuffle             # シャッフルする
=> ["n", "k", "q", "x", "d", "o", "h", "y", "t", "l", "s", "e", "g", "r", "u", "p", "c", "a", "m", "z", "b", "f", "w", "i", "v", "j"]
>> ('a'..'z').to_a.shuffle[0..7]       # 配列の冒頭8つの要素を取り出す
=> ["r", "s", "q", "b", "u", "d", "x", "v"]
>> ('a'..'z').to_a.shuffle[0..7].join  # 取り出した要素を結合して１つの文字列にする
=> "ftaoxijl"

// 演習
// 1.
>> (0..16).map { |i| i ** 2 }
=> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256]

// 2.
?> def yeller(array)
?>   array.map(&:upcase).join
>> end
=> :yeller
>> yeller(['o', 'l', 'd'])
=> "OLD"

// 3.
?> def random_subdomain
?>   ('a'..'z').to_a.sample(8).join
>> end
=> :random_subdomain
>> random_subdomain
=> "smahfpej"

// 4.
?> def string_shuffle(s)
?>   s.split('').shuffle.join
>> end
=> :string_shuffle
>> string_shuffle("foobar")
=> "foarob"
```

## ハッシュとシンボル

```bash
>> user = {}                          # {}は空のハッシュ
=> {}
>> user["first_name"] = "Michael"     # キーが "first_name" で値が "Michael"
=> "Michael"
>> user["last_name"] = "Hartl"        # キーが "last_name" で値が "Hartl"
=> "Hartl"
>> user["first_name"]                 # 要素へのアクセスは配列の場合と似ている
=> "Michael"
>> user                               # ハッシュのリテラル表記
=> {"first_name"=>"Michael", "last_name"=>"Hartl"}

// ハッシュロケットを用いたリテラル表現
>> user = { "first_name" => "Michael", "last_name" => "Hartl" }
=> {"first_name"=>"Michael", "last_name"=>"Hartl"}

// シンボル: 文字列とは異なる
>> "name".split('')
=> ["n", "a", "m", "e"]
>> :name.split('')
Traceback (most recent call last):
        1: from (irb):112
NoMethodError (undefined method `split' for :name:Symbol)
>> "foobar".reverse
=> "raboof"
>> :foobar.reverse
Traceback (most recent call last):
        1: from (irb):114
NoMethodError (undefined method `reverse' for :foobar:Symbol)

// シンボルでは、すべての文字列が使えるわけではない
>> :foo-bar
Traceback (most recent call last):
        2: from (irb):114
        1: from (irb):115:in `rescue in irb_binding'
NameError (undefined local variable or method `bar' for main:Object)
:> :2foo

// ハッシュのキーとしてシンボルを採用する
>> user = { :name => "Michael Hartl", :email => "michael@example.com" }
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}
>> user[:name]              # :name に対応する値にアクセスする
=> "Michael Hartl"
>> user[:password]          # 未定義のキーに対応する値にアクセスする
=> nil

// ハッシュでシンボルをキーとして使う場合の新しい記法
>> h1 = { :name => "Michael Hartl", :email => "michael@example.com" }
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}
>> h2 = { name: "Michael Hartl", email: "michael@example.com" }
=> {:name=>"Michael Hartl", :email=>"michael@example.com"}
>> h1 == h2
=> true

// ハッシュの中でハッシュを使うこともできる (ネストされたハッシュ)
>> params = {}        # 'params' というハッシュを定義する ('parameters' の略)。
=> {}
>> params[:user] = { name: "Michael Hartl", email: "mhartl@example.com" }
=> {:name=>"Michael Hartl", :email=>"mhartl@example.com"}
>> params
=> {:user=>{:name=>"Michael Hartl", :email=>"mhartl@example.com"}}
>> params[:user][:email]
=> "mhartl@example.com"

// ハッシュでも each を使える
>> flash = { success: "It worked!", danger: "It failed." }
=> {:success=>"It worked!", :danger=>"It failed."}
?> flash.each do |key, value|
?>   puts "Key #{key.inspect} has value #{value.inspect}"
>> end
Key :success has value "It worked!"
Key :danger has value "It failed."
=> {:success=>"It worked!", :danger=>"It failed."}

// `inspect` メソッド: 要求されたオブジェクトを表現する文字列を返す
>> puts (1..5).to_a            # 配列を文字列として出力
1
2
3
4
5
=> nil
>> puts (1..5).to_a.inspect    # 配列のリテラルを出力
[1, 2, 3, 4, 5]
=> nil
>> puts :name, :name.inspect
name
:name
=> nil
>> puts "It worked!", "It worked!".inspect
It worked!
"It worked!"
=> nil

// `p` メソッド: `inspect` メソッドを使いたい場合のショートカット
>> p :name             # 'puts :name.inspect' と同じ
:name
=> :name 
```

### 演習

#### 1.

下記のようなハッシュを定義する。

```ruby
hash = { 'one' => 'uno', 'two' => 'dos', 'three' => 'tres' }
```

その上で、下記のように出力する。

```ruby
hash.each do |key, value|
  puts "'#{key}' はスペイン語で '#{value}'"
end
```

```bash
>> hash = { 'one' => 'uno', 'two' => 'dos', 'three' => 'tres' }
=> {"one"=>"uno", "two"=>"dos", "three"=>"tres"}
?> hash.each do |key, value|
?>   puts "'#{key}' はスペイン語で '#{value}'"
>> end
'one' はスペイン語で 'uno'
'two' はスペイン語で 'dos'
'three' はスペイン語で 'tres'
=> {"one"=>"uno", "two"=>"dos", "three"=>"tres"}
```

#### 2.

3つのハッシュは次のように定義する。

```ruby
person1 = { first: 'Michael',   last: 'Hartl' }
person2 = { first: 'Shigeyuki', last: 'Fukuda' }
person3 = { first: 'Ryuta',     last: 'Matsuo' }
```

`params` ハッシュには、次のように代入していく。

```ruby
params = {}
params[:father] = person1
params[:mother] = person2
params[:child]  = person3
```

`params` ハッシュの値が合っているか、確認する。

```ruby
params[:father][:first] == person1[:first]
params[:mother][:first] == person2[:first]
params[:child][:first]  == person3[:first]
```

```bash
>> person1 = { first: 'Michael',   last: 'Hartl' }
=> {:first=>"Michael", :last=>"Hartl"}
>> person2 = { first: 'Shigeyuki', last: 'Fukuda' }
=> {:first=>"Shigeyuki", :last=>"Fukuda"}
>> person3 = { first: 'Ryuta',     last: 'Matsuo' }
=> {:first=>"Ryuta", :last=>"Matsuo"}
>> params = {}
=> {}
>> params[:father] = person1
=> {:first=>"Michael", :last=>"Hartl"}
>> params[:mother] = person2
=> {:first=>"Shigeyuki", :last=>"Fukuda"}
>> params[:child]  = person3
=> {:first=>"Ryuta", :last=>"Matsuo"}
>> params
=> {:father=>{:first=>"Michael", :last=>"Hartl"}, :mother=>{:first=>"Shigeyuki", :last=>"Fukuda"}, :child=>{:first=>"Ryuta", :last=>"Matsuo"}}
>> params[:father][:first] == person1[:first]
=> true
>> params[:mother][:first] == person2[:first]
=> true
>> params[:child][:first]  == person3[:first]
=> true
```

#### 3.

`user` ハッシュを定義する。

```ruby
user = { name: 'Michael Hartl', email: 'michael@x.com', password_digest: 'aaaaaaaaaaaaaaaa' }
```

```bash
>> user = { name: 'Michael Hartl', email: 'michael@x.com', password_digest: 'aaaaaaaaaaaaaaaa' }
=> {:name=>"Michael Hartl", :email=>"michael@x.com", :password_digest=>"aaaaaaaaaaaaaaaa"}
```

#### 4.

ruby-doc を見ると、 `merge` メソッドの引数にハッシュをとった場合、既存のキーに対応する値は上書きされる。

https://ruby-doc.org/3.2.2/Hash.html#method-i-merge

したがって、下記のコードは

```ruby
{ "a" => 100, "b" => 200 }.merge({ "b" => 300 })
```

次のようになると思われる。

```ruby
{ "a" => 100, "b" => 300 }
```

```bash
>> { "a" => 100, "b" => 200 }.merge({ "b" => 300 })
=> {"a"=>100, "b"=>300}
```

## CSS での記述

メソッド呼ぼだしの丸カッコは省略可能

```ruby
# メソッド呼び出しの丸カッコは省略可能。
stylesheet_link_tag('application', media: 'all',
                                   'data-turbolinks-track': 'reload')
# 上は以下のように書いても同じ
stylesheet_link_tag 'application', media: 'all',
                                   'data-turbolinks-track': 'reload'
```

ハッシュがメソッド呼び出しの最後の引数の場合、波括弧を省略可能。

```ruby
# 最後の引数がハッシュの場合、波カッコは省略可能。
stylesheet_link_tag 'application', { media: 'all',
                                     'data-turbolinks-track': 'reload' }
# 上は以下のように書いても同じ
stylesheet_link_tag 'application', media: 'all',
                                   'data-turbolinks-track': 'reload'
```

下記のコードでは、 `stylesheet_link_tag` メソッドを2つの引数で読んでいる。

```ruby
stylesheet_link_tag 'application', media: 'all',
                                   'data-turbolinks-track': 'reload'
```

## コンストラクタ

ダブルクォートは、文字列のオブジェクトを暗黙で作成するリテラルコンストラクタ。

```bash
>> s = "foobar"       # ダブルクォートは実は文字列のコンストラクタ
=> "foobar"
>> s.class
=> String
```

配列でも、文字列と同様にインスタンスを生成できる。

```bash
>> a = Array.new([1, 3, 2])
=> [1, 3, 2]
```

ハッシュの場合、デフォルト値を指定することができる。

```bash
>> h = Hash.new
=> {}
>> h[:foo]            # 存在しないキー (:foo) の値にアクセスしてみる
=> nil
>> h = Hash.new(0)    # 存在しないキーのデフォルト値をnilから0にする
=> {}
>> h[:foo]
=> 0
>> h
=> {}
```

### 演習

#### 1.

1から10の範囲オブジェクトを生成するリテラルコンストラクタは下記の通り。

```ruby
1..10
```

#### 2.

下記のようにして、範囲オブジェクトを生成できる。

```ruby
Range.new(1, 10)
```

```bash
>> Range.new(1, 10)
=> 1..10
```

#### 3.

比較してみる。

```bash
>> r1 = 1..10
=> 1..10
>> r2 = Range.new(1,10)
=> 1..10
>> r1 == r2
=> true
```

## クラス継承

`superclass` メソッドを使うと、 `クラス階層` を調べられる。
`String` クラスのスーパークラスは `Object` クラス。
`Object` クラスのスーパークラスは `BasicObject` クラス。
`BasicObject` クラスはスーパークラスを持たない。

```bash
>> s = String.new("foobar")
=> "foobar"
>> s.class                        # 変数sのクラスを調べる
=> String
>> s.class.superclass             # Stringクラスの親クラスを調べる
=> Object
>> s.class.superclass.superclass  # Ruby 1.9からBasicObjectが導入
=> BasicObject
>> s.class.superclass.superclass.superclass
=> nil
```

`Word` クラスを作成し、 `palindrome?` メソッドを作成する。

```bash
?> class Word
?>   def palindrome?(string)
?>     string == string.reverse
?>   end
>> end
=> :palindrome?

>> w = Word.new              # Wordオブジェクトを作成する
=> #<Word:0x00007fecf1fa9160>
>> w.palindrome?("foobar")
=> false
>> w.palindrome?("level")
=> true
>>
```

文字列を引数に取るのであれば、 `String` クラスを継承すべき。

```bash
?> class Word < String             # WordクラスはStringクラスを継承する
?>   # 文字列が回文であればtrueを返す
?>   def palindrome?
?>     self == self.reverse        # selfは文字列自身を表します
?>   end
>> end
=> :palindrome?

>> s = Word.new("level")    # 新しいWordを作成し、"level" で初期化する
=> "level"
>> s.palindrome?            # Wordが回文かどうかを調べるメソッド
=> true
>> s.length                 # WordはStringで扱える全てのメソッドを継承している
=> 5
```

`Word` クラスは `String` クラスを継承しているので、クラス階層を確認できる。

```bash
>> s.class
=> Word
>> s.class.superclass
=> String
>> s.class.superclass.superclass
=> Object
```

### 演習

#### 1.

`Range` クラスの継承クラスは下記の通り。

```bash
>> r = Range.new(1,10)
=> 1..10
>> r.class
=> Range
>> r.class.superclass
=> Object
>> r.class.superclass.superclass
=> BasicObject
```

また、 `Hash` クラスの継承クラスは下記の通り。

```bash
>> h = Hash.new
=> {}
>> h.class
=> Hash
>> h.class.superclass
=> Object
>> h.class.superclass.superclass
=> BasicObject
```

最後に、 `Symbol` クラスの継承クラスは下記の通り。

```bash
>> s = :name
=> :name
>> s.class
=> Symbol
>> s.class.superclass
=> Object
>> s.class.superclass.superclass
=> BasicObject
```

#### 2.

`WordSecond` クラスを作成する。

```ruby
class WordSecond < String
  def palindrome?
    self == reverse
  end
end
```

想定通りに動作するかチェックする。

```bash
?> class WordSecond < String
?>   def palindrome?
?>     self == reverse
?>   end
>> end
=> :palindrome?
>> w = WordSecond.new("level")
=> "level"
>> w.palindrome?
=> true
>> w.length
=> 5
```

## 組み込みクラスの変更

`String` クラスを拡張して、 `palindrome?` メソッドを追加する。

```bash
>> "level".palindrome?
Traceback (most recent call last):
        1: from (irb):37
NoMethodError (undefined method 'palindrome?' for "level":String)
?> class String
?>   # 文字列が回文であればtrueを返す
?>   def palindrome?
?>     self == self.reverse
?>   end
>> end
=> :palindrome?
>> "level".palindrome?
=> true
>> "deified".palindrome?
=> true
```

正当な理由がない限り、組み込みクラスにメソッドを追加するのは控えた方が良い。
Rails では、 `blank?` メソッドが追加されている。
`blank?` メソッドは、 `Object` クラスで定義されている。

```bash
>> "".blank?
=> true
>> "      ".empty?
=> false
>> "      ".blank?
=> true
>> nil.blank?
=> true
```

### 演習

#### 1.

それぞれ回文かどうかをチェックする。

```bash
>> "racecar".palindrome?
=> true
>> "onomatopoeia".palindrome?
=> false
>> "Malayalam".palindrome?
=> false
>> "Malayalam".downcase.palindrome?
=> true
```

#### 2.

`shuffle` メソッドは下記のようになると思われる。

```ruby
class String
  def shuffle
    self.split('').shuffle.join
  end
end
```

想定通りに動作するか、確認する。

```bash
?> class String
?>   def shuffle
?>     self.split('').shuffle.join
?>   end
>> end
=> :shuffle
>> "foobar".shuffle
=> "oobrfa"
```

#### 3.

`shuffle` メソッドから、 `self.` を削除してみる。

```ruby
class String
  def shuffle
    split('').shuffle.join
  end
end
```

想定通りに動作するか、確認する。

```bash
?> class String
?>   def shuffle
?>     split('').shuffle.join
?>   end
>> end
=> :shuffle
>> "foobar".shuffle
=> "abroof"
```

## コントローラクラス

Rails で定義したコントローラのクラス階層を調べる。

```bash
>> controller = StaticPagesController.new
=> #<StaticPagesController:0x00007fecf1245fa0 @_action_has_layout=true, @rendered_format=nil, @_routes=nil, @_request=nil, @_response=nil>
>> controler.class
Traceback (most recent call last):
        1: from (irb):67
NameError (undefined local variable or method 'controler' for main:Object)
Did you mean?  controller
               controller
               console
>> controller.class
=> StaticPagesController
>> controller.class.superclass
=> ApplicationController
>> controller.class.superclass.superclass
=> ActionController::Base
>> controller.class.superclass.superclass.superclass
=> ActionController::Metal
>> controller.class.superclass.superclass.superclass.superclass
=> AbstractController::Base
>> controller.class.superclass.superclass.superclass.superclass.superclass
=> Object
```

Rails コンソールでは、コントローラのアクションを呼ぶこともできる。

```bash
>> controller.home
=> nil
```

### 演習

#### 1.

`toy_app` アプリケーションで、 `user` オブジェクトが生成されることを確認する。

```bash
>> user = User.new
=> #<User id: nil, name: nil, email: nil, created_at: nil, updated_at: nil>
```

#### 2.

`user` オブジェクトの継承階層を調べる。

```bash
>> user.class
=> User(id: integer, name: string, email: string, created_at: datetime, updated_at: datetime)
>> user.class.superclass
=> ApplicationRecord(abstract)
>> user.class.superclass.superclass
=> ActiveRecord::Base
>> user.class.superclass.superclass.superclass
=> Object
```

## ユーザークラス

アプリケーションのルートディレクトリに `example_user.rb` ファイルを作成し、 `User` クラスを定義する。

```ruby
# example_user.rb

class User
  attr_accessor :name, :email

  def initialize(attributes = {})
    @name  = attributes[:name]
    @email = attributes[:email]
  end

  def formatted_email
    "#{@name} <#{@email}>"
  end
end
```

Rails コンソールで `User` クラスを使ってみる。

```bash
>> require './example_user'     # example_userのコードを読み込む方法
=> true
>> example = User.new
=> #<User:0x00007fece5c07860 @name=nil, @email=nil>
>> example.name                 # attributes[:name]は存在しないのでnil
=> nil
>> example.name = "Example User"           # 名前を代入する
=> "Example User"
>> example.email = "user@example.com"      # メールアドレスを代入する
=> "user@example.com"
>> example.formatted_email
=> "Example User <user@example.com>"
```

`initialize` メソッドにハッシュを渡スト、属性が定義済みのユーザーを作成できる。
これは、一般に *マスアサインメント (mass assignment)* と呼ばれ、 Rails アプリケーションでよく使われる。

```bash
>> user = User.new(name: "Michael Hartl", email: "mhartl@example.com")
=> #<User:0x00007fec972a6d00 @name="Michael Hartl", @email="mhartl@example.com">
>> user.formatted_email
=> "Michael Hartl <mhartl@example.com>"
```

### 演習

#### 1.

`User` クラスの定義を変更する。

```ruby
class User
  attr_accessor :first_name, :last_name, :email

  def initialize(attributes = {})
    @first_name = attributes[:first_name]
    @last_name  = attributes[:last_name]
    @email      = attributes[:email]
  end

  def full_name
    "#{@first_name} #{@last_name}"
  end

  def formatted_email
    "#{full_name} <#{@email}>"
  end
end
```

これが想定通りに動作するか、確認してみる。

```bash
>> require './example_user'
=> true
>> user = User.new(first_name: "Michael", last_name: "Hartl", email: "mhartl@example.com")
=> #<User:0x00007fece5d6fae0 @first_name="Michael", @last_name="Hartl", @email="mhartl@example.com">
>> user.full_name
=> "Michael Hartl"
>> user.formatted_email
=> "Michael Hartl <mhartl@example.com>"
```

#### 2.

`alphabetical_name` メソッドを定義する。

```ruby
class User
  .
  .
  .
  def alphabetical_name
    "#{@last_name}, #{@first_name}"
  end
end
```

想定通りに動作するか、確認する。

```bash
>> require './example_user'
=> true
>> user = User.new(first_name: "Michael", last_name: "Hartl", email: "mhartl@example.com")
=> #<User:0x00007fecc639a868 @first_name="Michael", @last_name="Hartl", @email="mhartl@example.com">
>> user.alphabetical_name
=> "Hartl, Michael"
```

#### 3.

同じ結果になるか、比較してみる。

```bash
>> user = User.new(first_name: "Michael", last_name: "Hartl", email: "mhartl@example.com")
=> #<User:0x00007fec9750da58 @first_name="Michael", @last_name="Hartl", @email="mhartl@example.com">
>> a1 = user.full_name.split
=> ["Michael", "Hartl"]
>> a2 = user.alphabetical_name.split(', ').reverse
=> ["Michael", "Hartl"]
>> a1 == a2
=> true
```

##
