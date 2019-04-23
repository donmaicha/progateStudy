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
オーバーライドしたメソッドの中で「super」とすることで、親クラスの同名のメソッドを呼び出すことができる。
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