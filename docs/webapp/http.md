---
layout: page
title: HTTP
parent: Webアプリケーションの仕組み
nav_order: 4
permalink: /webapp/http/
---

# HTTP

前提ページ：[クライアントサーバモデル](../client-server-model/)  
推奨ページ：[ウェブページの仕組み](../webpage/)

セキュアな Web サイトの作り方を学ぶ上で、Web サイトがどのように通信をしているかを知ることは重要です。このページでは Web 上の通信で利用される HTTP(S)について、学びます。

---

## 通信プロトコル

通信プロトコルとは、通信の手順やデータのフォーマットを決めたルール（規約）です。

プロトコルの例としては以下のようなものが挙げられます。

#### プロトコルの例

- HTTP
- FTP
- SSH

## HTTP

HTTP とは Web で利用される通信プロトコルです。

## HTTPS

HTTPS は HTTP に暗号化・改竄検出をさせたものです。
HTTPS を利用しましょう。

## HTTP(S) リクエストと HTTP(S) レスポンス

HTTP(S) はクライアントサーバモデルを採用しており、そのリクエストとレスポンスのことを、それぞれ HTTP(S) リクエスト、HTTP(S) レスポンスといいます。

![]({{ '/assets/images/http.png' | relative_url }})

## HTTP(S) リクエスト

HTTP リクエストは、HTTP リクエストヘッダと HTTP リクエストボディから成り立っています。

#### HTTP(S) リクエストの例

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

#### HTTP(S) リクエストヘッダの例

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
```

#### HTTP(S) リクエストボディ

```http
name=neko
```

## HTTP(S) レスポンス

HTTP レスポンスは、HTTP レスポンスヘッダと HTTP レスポンスボディ（＝対象のファイル）から成り立っています。

HTTP レスポンスボディの中身は、実際に要求するファイルと一致することになります。

#### HTTP(S) レスポンスの例

```http
HTTP/1.1 200 OK
Date: Sat, 30 Nov 2019 06:26:32 GMT
Server: Apache/2.4.38 (Debian)
Content-Encoding: gzip
Content-Length: 221
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html lang="ja">
  <head>
    <!-- headで囲まれた部分は見えない -->
    <meta charset="UTF-8" />
    <title>Hello</title>
  </head>
  <body>
    <!-- 見出し -->
    <h1>Hello, neko . </h1>
    <!-- 文字 -->
    <p>I'm akakou.</p>
  </body>
</html>
```

#### HTTP(S) レスポンスヘッダの例

```http
HTTP/1.1 200 OK
Date: Sat, 30 Nov 2019 06:26:32 GMT
Server: Apache/2.4.38 (Debian)
Content-Encoding: gzip
Content-Length: 221
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8
```

#### HTTP(S) レスポンスボディの例

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
    <h1>Hello, neko .</h1>
    <!-- 文字 -->
    <p>I'm akakou.</p>
  </body>
</html>
```
