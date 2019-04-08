# htmlcss学習メモ

## qml的な
* 幅、高さのプロパティはqmlと同じ
* ただし、指定する数字の後ろには単位必須(例: width: 70px)
* htmlのclassというものは、qmlでいうidに近い？
* item部品の中に3つ要素があった時、真ん中の部品のみプロパティを変えたいときに真ん中のid.widthなどと指定するが、それと似たような感じ
* borderは下だけ線を引くことも可能。その時はborder-bottomで指定する

## 絶対記述する箇所
### <meta charset="utf-8">
文字コード指定
UTF-8は、HTML5で推奨されている文字コード
### <tutle>hoge</title>
ブラウザに表示されるページタイトル
### <link rel="stylesheet" href="stylesheet.css">
rel="stylesheet"がcssを読み込む宣言<br>
href="stylesheet.css"が読み込むcssのファイル名

## 初知り
### float
float:left;で要素が左から横並びになる
paddingを指定すると、部品の内部marginを指定できる
padding-topで部品内部の上余白追加
下記記法は全て同じ意味
```css
.logo {
padding-top: 20px;
padding-right: 10px;
padding-bottom: 20px;
padding-left: 10px;
}
.logo {
padding: 20px 10px 20px 10px;
}
.logo {
padding: 20px 10px;
}
```

### <li>全体にcssが働いてしまう問題の解決法
```css
.header-list li {

}
.footer-list li {

}
```

## ブロック要素とインライン要素
### ブロック要素
前後で改行が入り、親要素いっぱいに広がる要素
* div
* h1
* p
### インライン要素
改行されない要素のこと
* span
* a
