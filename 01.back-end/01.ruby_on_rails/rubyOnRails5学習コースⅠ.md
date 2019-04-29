# Ruby on Rails5 学習コース Ⅰ
## railsアプリケーションの準備
> rails new tweet_app

railsで開発を始めるときは、上記の「rails new app名」というコマンドをターミナルで実行する<br>
このコマンドを実行することで、入力したapp名と同名のフォルダが作成され、その中に開発に必要なフォルダやファイルが用意される

## サーバーを立ち上げる
> rails server

ローカルホストのサーバを起動するための、上記のコマンドを実行する。<br>
サーバを起動したあと、ブラウザで「localhost:3000」というURLにアクセスすると、railsの画面が表示される。

## トップページを自動生成してみよう
> rails generate controller home top

トップページを作成するためには、上記のコマンドを実行する。<br>
このコマンドを実行すると、新しいwebページが自動で作成され、「localhost:3000/home/top」というURLにアクセスできるようになる。

