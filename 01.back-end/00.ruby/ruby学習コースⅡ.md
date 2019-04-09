# Ruby学習メモ
## ruby学習コースⅡ
### 配列
```ruby
array = ["山田", "田中", "佐藤"]
puts array
↓
#  改行されて表示される
山田
田中
佐藤
```
---
### 配列の変数展開
```ruby
puts "私の名前は#{array[1]}です"
↓
私の名前は田中です
```
---
### loop
#### each文
```ruby
names = ["Suzuki", "Kato", "Tanaka"]

names.each do |name|
  puts "名前は#{name}です"
end
```
---
### ハッシュ
#### 概要 
連想配列？構造体？よくわからず(TODO: 違いを調べる)<br>
ハッシュは、{キー1 => 値1, キー2 => 値2}のように作る。
```ruby
user = {"name" => "Suzuki", "age" => 21}
puts user
↓
{"name" => "Suzuki", "age" => 21}
```
#### 代入
```ruby
user = {"name" => "Suzuki", "age" => 21}
user["age"] = 22
puts user
↓
{"name" => "Suzuki", "age" => 22}
```
#### 要素の追加
```ruby
user = {"name" => "Suzuki", "age" => 21}
user["gender"] = "male"
puts user
↓
{"name" => "Suzuki", "age" => 22, "gender" => "male"}
```
#### シンボル
ハッシュは、キーの部分を文字列ではなく、先頭にコロン「:」を付けた書き方をすることもできる。<br>
この「:name」という書き方のことをシンボルと言う。(TODO: どっちが主流なのか調べる)
```ruby
{"name" => "Suzuki", "age" => 21}
↓
{:name => "Suzuki", :age => 21}
```
シンボルとは、文字を「"」や「'」で囲む代わりに、先頭に「:」をつけた書き方のことを指す。<br>
文字列とシンボルは厳密には異なりますが、基本的には同じように使用することができる。(TODO: どこに違いがあるのか調べる)
```ruby
# 出力結果は同じ
puts "ruby"
puts :ruby
```
シンボルは、ハッシュのキーとしてよく使われる。<br>
ハッシュのキーの部分を「:name」という様に、シンボルを用いた場合には、その値を用いる時も「user[:name]」とシンボルで指定する必要がある。<br>この際、キーに文字列を指定してもうまくいかないので注意。
#### ハッシュを省略した書き方
ハッシュのキーにシンボルを用いるときには、省略した書き方をすることができる。<br>
具体的には「:key =>」を「key:」というように省略することができる。
```ruby
{:name => "Suzuki", :age => 21}
↓
{name: "Suzuki", :age: 21}
```
省略した書き方の場合でも、あくまでキーはシンボルなので、要素を取得する場合には以下のようにシンボルを用いる必要がある。
```ruby
user = {name: "Suzuki", :age: 21}
puts user[:name] # 省略した場合もシンボルを用いて要素を取得する
```
---
### nil
ハッシュから存在しないキーの値を取り出した時の「何もない」という値は、Rubyでは「nil」(読み方：ニル)という特別な値で表現される。<br>
「nil」は「何もない」という意味なので、putsしても何も表示されない。<br>
nullと何が違うの？(TODO:後で調べる)
#### ifとnil
実は、ifの条件には、真偽値(trueとfalse)以外も使うことができる。<br>
Rubyでは、ifの条件に真偽値以外を用いたとき、それがnilであればfalseとして扱われ、それ以外はtrueとして扱われる。
```ruby
user = {name: "Suzuki", age: 21}
if user[:age]
  puts "#{user[:name]}さんは#{user[:age]歳です}"
else 
  puts "#{user[:name]}さんの年齢は秘密です}"
end
↓
Suzukiさんは21歳です
```
```ruby
user = {name: "Suzuki"}
if user[:age]
  puts "#{user[:name]}さんは#{user[:age]歳です}"
else 
  puts "#{user[:name]}さんの年齢は秘密です}"
end
↓
Suzukiさんの年齢は秘密です
```
---
### 配列の要素にハッシュを入れる
配列の要素には、文字列や数値だけでなく、ハッシュも使うことができるので、左の図のような配列を作ることができる。
```ruby
users = [
  {name: "Suzuki", age: 21},
  {name: "Kato"  , age: 14}
]
puts users[1]
↓
{:name => "Kato" , :age => 14}
```
```ruby
users = [
  {name: "Suzuki", age: 21},
  {name: "Kato"  , age: 14}
]
puts users[1][:name]
↓
Kato
```
### eachの中でハッシュ値を使う
```ruby
users = [
  {name: "Suzuki", age: 21},
  {name: "Kato"  , age: 14}
]
users.each do |user|
  puts user[:name]
end
↓
Suzuki
Kato
```
### 演習
#### オリンピックの開催年と開催場所
```ruby
olympics = [
  {year: 1896, city: "アテネ"},
  {year: 1900, city: "パリ"},
  {year: 1904, city: "セントルイス", note: "アメリカ初開催"},
  {year: 1908, city: "ロンドン"},
  {year: 1912, city: "ストックホルム"},
  {year: 1916, city: "ベルリン", note: "第一次世界大戦で中止"},
  {year: 1920, city: "アントワープ"},
  {year: 1924, city: "パリ", note: "同じ都市での2回目の開催は初"},
  {year: 1928, city: "アムステルダム"},
  {year: 1932, city: "ロサンゼルス"}
]

puts "第1~10回大会のオリンピック一覧"

olympics.each do |olympic|
  puts "---------------------"
  puts "#{olympic[:year]}年#{olympic[:city]}大会"
  
  # 豆知識がある場合のみ豆知識について出力
  if olympic[:note] != nil
    puts "豆知識:#{olympic[:note]}"
  end
end
```