---
layout: page
title: HTTPメソッドとパラメータ
parent: Webアプリケーションの仕組み
nav_order: 5
permalink: /webapp/http-method
---

# HTTP メソッドとパラメータ

前提ページ：[HTTP](../http.md)、[HTTP ヘッダ](../http-headers.md)  
推奨ページ：[クライアントサーバモデル](../client-server-model/)

セキュアな Web サイトの作り方を学ぶ上で、Web サイトがどのように通信をしているかを知ることは重要です。このページでは Web 上の通信で利用される HTTP(S)のメソッドについて、学びます。

---

## HTTP メソッド

HTTP メソッドとは、アクセスしたいサーバ上のリソース（ファイル等）に対して、どのような操作をしたいのかを表すものです。

#### HTTP メソッドの有名所

| メソッド |      意味      |
| :------: | :------------: |
|   GET    | リソースの取得 |
|   POST   | リソースの追加 |
|   PUT    | リソースの更新 |
|  PATCH   | リソースの更新 |
|  DELETE  | リソースの消去 |

---

## サーバへのデータの送信

Web アプリケーションでは、クライアントがサーバに対して、なにか情報を伝えたい場合があります。
例えばショッピングサイトでは、ユーザが何をカートに入れて、何を注文確定させたか、ブラウザがサーバに対して伝える必要があります。

## リクエスト パラメータ（クエリストリング / GET パラメータ）

主に GET メソッド で利用されるパラメータです。
URL の最後にキーとそれに対する値を入れて、サーバに伝えます。

#### URL 例

- `http://127.0.0.1?key1=value1&key2=value2`
- `http://127.0.0.1?name=fizz`

#### リクエスト パラメータを送信する HTML 例

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
    <h1>What's your name?</h1>
    <!-- 文字 -->
    <form action="hello.php" method="get">
      <input name="name" type="text" />
      <input type="submit" value="submit" />
    </form>
  </body>
</html>
```

#### 受け取る PHP 例

```php
<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- headで囲まれた部分は見えない -->
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <!-- 見出し -->
    <h1>
      Hello,
      <!-- ここでGETパラメータを受け取ってそのまま表示 -->
      <?php echo $_GET['name']?>.
    </h1>
    <!-- 文字 -->
    <p>I'm akakou.</p>
  </body>
</html>
```

#### 送信する HTTP リクエスト例

```http
GET /hello.php?name=neko HTTP/1.1
Host: localhost:4002
Connection: keep-alive
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Referer: http://localhost:4003/
Accept-Encoding: gzip, deflate, br
Accept-Language: ja,en;q=0.9
```

## POSTパラメータ

主に POST メソッド で利用されるパラメータです。
HTTPリクエストボディにパラメータを入れます。

#### リクエスト パラメータを送信する HTML 例

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
    <h1>What's your name?</h1>
    <!-- 文字 -->
    <form action="hello.php" method="post">
      <input name="name" type="text" />
      <input type="submit" value="submit" />
    </form>
  </body>
</html>
```

#### 受け取る PHP 例

```php
<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- headで囲まれた部分は見えない -->
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <!-- 見出し -->
    <h1>
      Hello,
      <!-- ここでGETパラメータを受け取ってそのまま表示 -->
      <?php echo $_POST['name']?>.
    </h1>
    <!-- 文字 -->
    <p>I'm akakou.</p>
  </body>
</html>
```

#### 送信する HTTP リクエスト例

```http
POST /hello.php HTTP/1.1
Host: 127.0.0.1:4001
Connection: keep-alive
Content-Length: 9
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Referer: http://127.0.0.1:4001/
Accept-Encoding: gzip, deflate, br
Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0

name=neko
```
