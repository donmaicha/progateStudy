# Ruby on Rails5 学習コース Ⅲ

## 自動生成されるカラム
### idカラム
データベースに保存される時、数字が自動で入る。<br>
idは1から順に入っていき、データごとに重複しないようになっている。

### created_atカラムとupdated_atカラム
データベースに保存された時刻が自動で入る。<br>
updated_atはデータ更新時にも時刻が更新される。

## find_byメソッドで投稿を取得する
特定のidの投稿を取得するために用いる。<br>
find_byメソッドは、ある条件に合致するデータを取得することができる。<br>
「モデル名.find_by(カラム名: 値)」とすることで、その値を持ったデータをデータベースから取得することができる。
```ruby
post = Post.find_by(id:3)
puts post.content # postsテーブルの3番目のcontentが出力される
```

## URLにidを含める
ルーティングのURL部分に「:」を用いて「posts/:id」と指定することで、「/posts/1」でも「/posts/2」でもshowアクションにいくようになる。
「posts/:id」と書くと「/posts/◯◯」のような全てのURLが該当する。
(メリット)これをしないと新規データが作られた時、ルーティングも新たに作成しなければならなく、冗長だから
```ruby
get "posts/:id" => "posts#show"
```

## URLからidを取得する
コントローラのアクション内では、ルーティングで設定したURLの「:id」の値を取得することができる。<br>
その値はparamsという変数にハッシュとして入っており、params[:id]とすることで、その値を取得することができる。
```ruby
def show
  @id = params[:id] # {id: 1}というハッシュがparamsに入っている
end
```

## 詳細画面に投稿を表示する
```ruby
def show 
  @post = Post.find_by(id: params[:id]) # idカラムがparams[:id]である投稿データを取得している
end
```
## 詳細ページへのリンクを作る
各投稿の内容の部分をクリックすると詳細ページに移動できるように、link_to(post.content, "/posts/#{post.id}")とする。
```html
<% @posts.each do |post| %>
  <div class="posts-index-item">
    <%= link_to(post.content, "/posts/#{post.id}") %>
  </div>
<% end %>
```