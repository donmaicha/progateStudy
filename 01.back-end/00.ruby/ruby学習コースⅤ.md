# Ruby学習メモ
## ruby学習コースⅣ
### 継承
「class 新しいクラス名 < 元となるクラス名」とすることで他のクラスを継承して、新しいクラスを定義することができる。
```ruby
class Food < Menu # 子クラス(Food)に親クラス(Menu)を継承

end
```
### インスタンス変数の追加
子クラスにインスタンス変数を追加するためには、これまで通り「attr_accessor」を用いる。<br>
以下のFoodクラスの例では、親クラスで定義してあるnameとpriceに加え、新たに追加したcalorieというインスタンス変数を用いることができる。
```ruby
class Food < Menu
  # foodクラスにcalorieを追加
  attr_accessor :calorie
end
```

### メソッド内の重複
```ruby
class Menu
  def initialize(name:, price:)
  # ☆
    self.name = name 
    self.price = price 
  end
end

class Food < Menu
  def initialize(name:, price:)
  # ☆と同じ処理をしているため、冗長な感じがする・・・
    self.name = name 
    self.price = price
  end
end
```
**superを使えばまとめることができる！**
オーバーライドしたメソッドの中で「super」とすることで、親クラスの同名のメソッドを呼び出すことができる。<br>
あくまでメソッドを呼び出しているので、親クラスのメソッドの定義に合わせて、superに対して引数を渡す必要がある。

```ruby
class Menu
  attr_accessor :name
  attr_accessor :price

  def initialize(name:, price:)
    self.name = name
    self.price = price
  end
end

class Food < Menu
  attr_accessor :calorie

  def initialize(name:, price:, calorie:)
    super(name: name, price: price) # 親クラスの同名メソッドを呼び出す
    self.calorie = calorie
  end
end
```
### ruby既存の組み込みクラスの使い方
```ruby
# Dateクラスの読み込み
# ※"./dateでないことに注意"
require "date"

date1 = Date.new(2014, 7, 31)
puts date1
puts date1.sunday? # date1が日曜日かどうか判定
date2 = Date.today
puts date2
↓
出力: 2014-07-31
      false
      2019-04-24
```
### クラスメソッドの定義
```ruby
class Menu
  def Menu.is_discount_day?
    # 処理
  end
end
```
### クラスメソッドの中でDateクラスを用いる
```ruby
require "date"

class Menu
  def Menu.is_discount_day?
    today = Date.today
  end
end

```

### クラスメソッドを呼び出す
クラスメソッドは定義時と同じように、「クラス名.メソッド名」とすることで呼び出せる
```ruby
class Menu
  def Menu.is_discount_day?
  
  end  
end

puts Menu.is_discount_day?
```

### インスタンスメソッドの中でクラスメソッドを呼び出す
クラスメソッドはクラスの中でも、同じように呼び出すことができる。<br>
下記、Menuクラスのインスタンスメソッドである「get_total_price」メソッドの中で、クラスメソッド「is_discount_day?」を呼び出す例になる
```ruby
class Menu
  def get_total_price # インスタンスメソッド
    if Menu.is_discount_day? # クラスメソッドの呼び出し

    end 
  end
end
```

### インスタンスメソッドとクラスメソッド
```ruby
# インスタンスメソッド
class Menu
  def info # インスタンスメソッドの定義
    # hoge
  end
end

menu1 = Menu.new
menu1.info # インスタンスメソッドはインスタンスに対して呼び出す
```
```ruby
# クラスメソッド
class Menu
  def Menu.is_discount_day?
    # fuga
  end
end

Menu.is_discount_day? # クラスメソッドはクラスに対して呼び出す
```
