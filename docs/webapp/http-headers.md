---
layout: page
title: HTTP ヘッダ
parent: Webアプリケーションの仕組み
nav_order: 5
permalink: /webapp/http-headers/
---

# HTTP ヘッダ

前提ページ：[HTTP](../http/)  
推奨ページ：なし

セキュアな Web サイトの作り方を学ぶ上で、Web サイトがどのように通信をしているかを知ることは重要です。このページでは Web 上の通信で利用される HTTP(S)のヘッダについて、学びます。

---

## HTTP リクエストヘッダ

以下のような HTTP リクエストの上部※を HTTP リクエストヘッダと呼びます。
HTTP リクエストヘッダでは行の左側にヘッダー名を、右側に値を入れることが多いです。

#### HTTP リクエストヘッダの例

```http
POST /hello.php HTTP/1.1
Host: 127.0.0.1:4001
Connection: keep-alive
Content-Length: 9
Cache-Control: max-age=0
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Referer: http://127.0.0.1:4001/
Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0
```

## 各ヘッダーに対する解説

覚えておくと良いものだけ、解説します。

### {method} {uri} HTTP/{version}

例：`POST /hello.php HTTP/1.1`（1 行目）

`{method}`は HTTP メソッドの値です。`GET`、`POST`、`PUT`、`PATCH`、`DELETE`などが入ります。※1

`{uri}`はサーバのどこにそのファイルがあるかを指定するものです。

`version`は HTTP のバージョンを表します。

### Host: {host}

例：`Host: 127.0.0.1:4001`（2 行目）

`{host}`には サーバ自身のいる場所（IP アドレス等）が入ります。※2

### Content-Length: {length}

例：`Content-Length: 9`（4 行目）

`{length}`には、HTTP リクエストボディのサイズ（バイト）が入ります。

### Content-Type: {type}

例：`Content-Type: application/x-www-form-urlencoded`（6 行目）

`{type}`はリクエストボディがどのようなデータを持っているかの種類が入ります。

#### `{type}`として使われる例

| Content-Type | ファイルの種類 |
| text/plain | テキスト |
| text/csv | CSV |
| text/html | HTML |
| text/css | CSS |
| text/javascript |JavaScript |
| application/json | JSON |
| application/pdf | PDF |
| image/jpeg | JPEG |
| image/png | PNG |
| image/gif | GIF |
| video/mp4 | MP4 |

### User-Agent: {agent}

例：`User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.97 Safari/537.36`（7 行目）

`{agent}`はどのような種類のブラウザを利用しているかの情報が送られます。

### Accept: {accept}

例：`Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3`（8 行目）

`{accept}`ではサーバがどのようなデータをレスポンスボディに返すかの指定をします。

### Referer: {referer}

例：`http://127.0.0.1:4001/`（9 行目）

`{referer}`には、このページにアクセスする一個前のページの URL が入ります。

### Cookie: {cookies}

例：`Cookie: \_ga=GA1.1.11882848.1574929583; \_ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（10 行目）

`{cookies}`は複数の cookie※のキーとそれに対応する値を持ちます。
