---
layout: page
title: ウェブページの仕組み
parent: Webアプリケーションの仕組み
nav_order: 1
---

# ウェブページの仕組み

セキュアな Web サイトの作り方を学ぶ上で、Web ページがどのように構成されているかを知ることは、重要なことです。

この章では Web ページを構成する言語、そしてブラウザについて学びます。

## 仕組み

私達はサーバというコンピュータから送られてきた、プログラムのファイル（主に HTML、CSS、Javascript）をブラウザ上で実行し、結果を画面に出力することで、ウェブページを見ることができています。

![]({{ '/assets/images/browser.png' | relative_url }})

## HTML

HTML(HyperText Markup Language)とは、ウェブページを作るための言語です。
文字やボタン、画像をおくなどができます。

#### コード 1. HTML の例

以下の例では、h1 タグを用いて見出し（要は大きな文字）を、p タグを用いて文字列を画面上においています。

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- headで囲まれた部分は見えない -->
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <!-- 見出し -->
    <h1>Hello, everyone!</h1>
    <!-- 文字 -->
    <p>I'm akakou.</p>
  </body>
</html>
```

## Javascript

HTML によって表されるウェブページに動的な変更を加えるために利用される言語です。
例えば、ボタンを押したときに画面の一部が変更されるなどの処理は、Javascript で記述されることが多いです。

#### コード 2. 動的に HTML を動かす例

以下のウェブページ例では、ボタンを押したときに画面の一部が変更されます。

##### /index.html

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- headで囲まれた部分は見えない -->
    <meta charset="UTF-8" />
    <title>Hello</title>

    <!-- Javascriptのファイルを読み込んでいる -->
    <script src="/script.js"></script>
  </head>
  <body>
    <!-- 見出し -->
    <p id="output">I'm akakou.</p>
    <!-- 入力フォーム -->
    <input id="input" type="text" />
    <!-- ボタン -->
    <button onsubmit="submit()">run</button>
  </body>
</html>
```

##### /script.js

```js
function submit() {
  /**
   * 入力フォームの値を取得して、
   * 画面に文字列として表示する
   **/
  var input = document.getElementById("input");
  var output = document.getElementById("output");
  output.innerText = input.value;
}
```

## CSS

CSS（Cascading Style Sheets）は、Web ページのスタイル（見た目）を決定するための言語です。
今回 CSS に関する例は割愛します。

## ブラウザ

HTML、CSS、Javascript を実行し、画面に結果を出力したりするプログラムであり、例としては Chrome、Firefox、Edge などが挙げられます。

# 備考

※ 特に[セキュアプログラミングの章（未公開）]()、[脆弱性の章（未公開）]()を学びたい方は、これらの言語（HTML、CSS、Javascript）をよく理解しておくと良いと思います。個人的なおすすめは、[Progate](https://prog-8.com/languages/html)です。
