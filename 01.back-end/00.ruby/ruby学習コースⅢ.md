# Ruby学習メモ
## ruby学習コースⅢ
### 関数
#### 書き方
```ruby
# 宣言
def introduce
  puts "こんにちわ"
  puts "わたしはにんじゃわんこです"
end

# 呼び出し方
introduce # ()が必要ないの？
```
#### 引数
```ruby
def introduce(name, age)
  puts "こんにちわ"
  puts "わたしは#{name}です"
  puts "#{age}歳です"
end

introduce("にんじゃわんこ", 14)
introduce("ひつじ仙人", 16)
```
#### 戻り値のある関数
```ruby
def add(a, b)
  return a + b
end
sum = add(1, 3)
puts sum
↓
4
```
#### 様々な戻り値
if文で使うような条件式をreturnすると、その条件式の結果として得られる真偽値（trueまたはfalse）を返すことができる。<br>
真偽値を返すメソッドは、メソッド名の末尾に「?」をつける慣習がある。
```ruby
def negative?(number)
  return number < 0
end
puts negative?(5)
↓
false
```
#### キーワード引数
```ruby
def introduce(name:, age:, food:) # 引数の後にコロンをつける
  puts "私の名前は#{name}です"
  puts "年齢は#{age}歳です"
  puts "好きな食べ物は#{food}です"
end

introduce(name: "にんじゃわんこ", age: 14, food: "ラーメン") # 値の前に引数名を書く
```