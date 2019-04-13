# Ruby学習メモ
## ruby学習コースⅣ
### クラス
#### 書き方
```ruby
# クラスは大文字から始める
class Menu

end
```
#### インスタンス変数
情報を持たせるためには、「attr_accessor シンボル」と書く
```ruby 
class Menu
  attr_accessor :name
  attr_accessor :price
end
```
#### インスタンスの生成
クラスを元に、新しくインスタンスを生成するには、「クラス名.new」と書く。<br>
また、「変数名 = クラス名.new」とすることで、生成したインスタンスを変数に代入することができます。
```ruby
menu1 = Menu.new
menu1.name = "すし"
puts menu1.name
↓
すし
```
#### インスタンスメソッド
```ruby
class Menu
  def show(data)
    puts "私は#{data}です"
  end
end

menu1 = Menu.new
menu1.show("メニュー")
↓
わたしはメニューです
```

#### インスタンスメソッドの中でインスタンス変数を利用する
```ruby
class Menu
  attr_accessor :name
  def show_name
    puts "私は#{self.name}です"
  end
end

menu1 = Menu.new
menu1.name = "ピザ"
menu1.show_name
↓
私はピザです
```
#### initialize
initializeメソッドは、「クラス名.new」でインスタンスを生成した直後に自動で呼び出される。
1. Menu.newが実行される
2. 空のMenuインスタンス生成
3. 生成されたインスタンスに対し、initializeメソッドが自動で呼び出される
```ruby
def initialize
  puts "メニューが作成されました"
end

menu1 = Menu1.new
↓
メニューが作成されました
```
#### initializeメソッドの引数
「クラス.new」に対して引数を渡すことで、initializeメソッドにその値を渡すことが可能。
```ruby
class Menu
  def initialize(message:)
    puts message
  end
end
menu1 = Menu.new(message: "こんにちは”)
↓
こんにちは
```
#### require
index.rbの一番上の行で、「require "./menu"」とすることで、menu.rbのコードを読み込めるようになる<br>
pythonでいうimport?
```ruby
require "./menu"

menu1 = Menu.new(name)
```
#### インスタンスの配列
Menuクラスから生成したインスタンスも、配列の要素にすることが可能。<br>
各インスタンスを要素とする配列を変数menusに代入し、その配列に対してeach文を用いることで、それぞれのメニューを表示することができる。
```ruby
menu1 = Menu.new(name: "ピザ", price: 800)
menu2 = Menu.new(name: "すし", price: 1000)
menu3 = Menu.new(name: "にく", price: 1800)
menu4 = Menu.new(name: "ケーキ", price: 400)

menus = [menu1, menu2, menu3, menu4]

menus.each do |menu|
  puts menu.info
end
```
#### 繰り返し処理で番号をつける
```ruby
fruits = ["apple", "banana", "orange"]
index = 0
fruits.each do |fruit|
  puts "#{index}.#{fruit}"
  index++
end
```
#### 標準入力を受け取る
「変数 = gets.chomp」とすることで、エンターキーを押されるまでに入力された値を変数に代入することができる。
```ruby
puts "名前を入力してください"

name = gets.chomp
puts "あなたのなまえは#{name}です"
```
「gets.chomp」で入力された値を受け取ることができましたが、実はこれは文字列になるため、「3」と入力しても文字列の"3"になってしまう。<br>
数値の計算などに用いる場合は、これを数値に変換する必要がある。<br>
「gets.chomp.to_i」と書くことで、入力された内容を数値に変換し、計算などにも使えるようになる。
```ruby
puts "数字を入力してください"
number = get.chomp.to_i
puts "#{number}の2倍は#{number * 2}です"
```