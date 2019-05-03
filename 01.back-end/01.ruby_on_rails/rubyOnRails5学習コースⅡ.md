# Ruby on Rails5 学習コース Ⅱ

## postsControllerを作成する
今回は、投稿に関するページを作成するため、postsControllerを作成する。<br>
homeコントローラでも作成することができるが、投稿に関することは投稿に関するコントローラを作成したほうがよい。<br>
一覧ページを作成する時は、indexというアクション名を使用することが一般的なので、indexアクションを用意する。<br>
今回は新しくpostsコントローラを作成するので、「rails g controller posts index」を実行する。<br>
「rails generate controller」は「rails g controller」と省略可。

## viewファイル内で変数を定義する
index.html.erbのようなerbという形式のファイルでは、<% %>で囲むことで、HTMLファイルの中にRubyのコードを記述することができる。<br>
「erb」とは「Embedded Ruby（埋め込みRuby）」の略。
```html
<!-- Rubyのコード -->
<% post1 = "今日からProgateでRails" %>
<% post2 = "投稿一覧ページ作成中!" %>

<div class="posts-index">
<div>
```
埋め込むRubyコードをブラウザに表示したい場合には、以下のように<% %>ではなく、<%= %>を用います。
```html
<% post1 = "今日からProgateでRails" %>

<%= post1 %>
```