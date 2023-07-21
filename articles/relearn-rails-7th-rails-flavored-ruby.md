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


##
