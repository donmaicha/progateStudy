# Ruby on Rails5 学習コース Ⅳ

## 投稿を編集する
```ruby
# id:1のcontentをRailsに編集する
post = Post.find_by(id: 1)
post.content = "Rails"
post.save # save時に、updated_atが自動的に更新される
```

## 投稿を削除する
```ruby
# id:2のレコードを削除する
post = Post.find_by(id: 2)
post.destroy
```

## 投稿編集ページを作成する
```ruby
get "posts/:id/edit" => "posts#edit"
# 編集したい投稿のidをURLに含む。
# 「localhost: 3000/posts/1/edit」
# 「localhost: 3000/posts/2/edit」
# などのURLに対応させる
```
## 投稿編集ページへのリンクを追加する
```html
<!-- editアクションのURLを指定 -->
<%= link_to("編集", "/posts/#{@post.id}/edit") %>
```

## フォームに初期値を用意する
textareaタグでは、タグで囲んだ部分を初期値として設定できる。
```html
<textarea>にんじゃわんこ</textarea>
```
![textareaの初期値](img/textareaの初期値.PNG)

## 投稿内容をフォームの初期値にする
フォームの初期値として、編集したい投を表示するため、<br>
editアクションで、URLのidと同じidの投稿データをデータベースから取得し、<br>
そのcontentの値(=投稿の内容)を初期値に設定する
```ruby
def edit
  # {id: 1}というハッシュが変数paramsに入っている
  @post = Post.find_by(id: params[:id])
end
```
```html
<!-- 初期値として入力される -->
<textarea><%= @post.content %></textarea>
```
