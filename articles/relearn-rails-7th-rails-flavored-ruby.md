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

##
