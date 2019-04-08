# htmlcss学習メモ
##Rubyの基本
### 標準出力
```ruby
puts 'Hello World'
```
### コメント
```ruby
# Hello Worldと出力します
puts 'Hello World'
```
### 変数
pythonと同じように、型の宣言が不要
```ruby
name = "John"
puts name
```
### 変数名のルール
スネークケースがスタンダード
```ruby
  # クラス名: アッパーキャメルケース
  MyClass
  # メソッド名: スネークケース
  update_attribute
  # 変数名: スネークケース
  user_name
```
### 変数展開
ダブルクォーテーションで囲った文字列でのみ使用可能<br>
シングルクォーテーションで囲った文字列で行うと、そのまま文字として出力されてしまう
```ruby
name = "佐藤"
puts "こんにちは#{name}さん"
age = 19
puts "#{age}歳です"
```
### if文の書き方
```ruby
score = 95
if score > 80
  puts "よくできました"
elsif score > 60
  puts "まずまずです"
else 
  puts "がんばりましょう"
end
```
