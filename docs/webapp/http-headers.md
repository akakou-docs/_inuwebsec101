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

他の章を読むのに、すべてを理解する必要はありません。**読み飛ばして構いませんので、必要なところだけ読んでください。**

---

## HTTP リクエストヘッダ

以下のような HTTP リクエストの上部（２つある改行より上）を HTTP リクエストヘッダと呼びます。
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

`{uri}`はサーバのどこにそのファイルがあるかを指定するものです。

`{method}`は `{uri}`のファイルがに対してどうしたいか（取得・新規作成・変更・消去など）を表すもので、これを HTTP メソッドと呼びます。`GET`、`POST`、`PUT`、`PATCH`、`DELETE`などが入ります。 ※1

`version`は HTTP のバージョンを表します。

### Host: {host}

例：`Host: 127.0.0.1:4001`（2 行目）

`{host}`には サーバ自身のいる場所（IP アドレス、ドメイン等）が入ります。

### Content-Length: {length}

例：`Content-Length: 9`（4 行目）

`{length}`には、HTTP リクエストボディのサイズ（バイト）が入ります。

### Content-Type: {type}

例：`Content-Type: application/x-www-form-urlencoded`（6 行目）

`{type}`はリクエストボディがどのようなデータを持っているかの種類が入ります。

#### `{type}`として使われる例

|   Content-Type   | ファイルの種類 |
| :--------------: | :------------: |
|    text/plain    |    テキスト    |
|     text/csv     |      CSV       |
|    text/html     |      HTML      |
|     text/css     |      CSS       |
| text/javascript  |   JavaScript   |
| application/json |      JSON      |
| application/pdf  |      PDF       |
|    image/jpeg    |      JPEG      |
|    image/png     |      PNG       |
|    image/gif     |      GIF       |
|    video/mp4     |      MP4       |

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

例：`Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（10 行目）

`{cookies}`は複数の cookie というブラウザ側で保存できるデータとそれに対応するキーを持ちます。 ※1

---

## HTTP リクエストヘッダ

以下のような HTTP レスポンスの上部（２つある改行より上）を HTTP レスポンスヘッダと呼びます。
HTTP レスポンスヘッダでは行の左側にヘッダー名を、右側に値を入れることが多いです。

#### HTTP リクエストヘッダの例

```http
HTTP/1.1 200 OK
Date: Sat, 30 Nov 2019 06:26:32 GMT
Server: Apache/2.4.38 (Debian)
Content-Encoding: gzip
Content-Length: 221
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8
Set-Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0
```

## 各ヘッダーに対する解説

覚えておくと良いものだけ、解説します。

### HTTP/{version} {status_code}

例：`POST /hello.php HTTP/1.1`（1 行目）

`version`は HTTP のバージョンを表します。

`{status_code}`は、ステータスコードと言われ、サーバからのレスポンスの意味を表します。

よく使われる`{status_code}`は以下のとおりです。

#### ステータスコード一覧

|     ステータスコード      | 意味                                                                                                                                                         |
| :-----------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
|          200 OK           | リクエストが成功したことを示します。                                                                                                                         |
|        201 Created        | リクエストは成功し、その結果新たなリソースが作成されたことを示します。                                                                                       |
|   301 Moved Permanently   | リクエストされたリソースの URL が永遠に変更されたことを示します。レスポンスで新しい URL が与えられます。                                                     |
|     304 Not Modified      | このレスポンスコードはクライアントに対して、レスポンスは変更されていないことを示します。<br>よって、クライアントはキャッシュ済みのレスポンスを使い続けます。 |
|      400 Bad Request      | 構文が無効であるためサーバーがリクエストを理解できないことを示します。                                                                                       |
|     401 Unauthorized      | HTTP 標準では "unauthorized" (不許可) と定義されていますが、意味的にはこのレスポンスは "unauthenticated" (未認証) です。                                     |
|       403 Forbidden       | 認証されていないなどの理由でクライアントにコンテンツのアクセス権がなく、サーバーが適切なレスポンスの返信を拒否していることを示します。                       |
|       404 Not Found       | サーバーがリクエストされたリソースを発見できないことを示します。                                                                                             |
|  405 Method Not Allowed   | サーバーがリクエストメソッドを理解しているものの、無効にされており使用することができません。                                                                 |
| 500 Internal Server Error | サーバー側で処理方法がわからない事態が発生したことを示します。                                                                                               |
|  503 Service Unavailable  | サーバーはリクエストを処理する準備ができていないことを示します。一般的な原因は、サーバーがメンテナンスや過負荷でダウンしていることです。                     |

### Server: {server_type}

例：`Server: Apache/2.4.38 (Debian)`（3 行目）

`{server_type}`はサーバの種類を表します。

### Content-Length: {length}

例：`Content-Length: 221`（5 行目）

`{length}`にはレスポンスボディのサイズ（バイト）が入ります。

### Content-Type: {type}

例：`Content-Type: text/html; charset=UTF-8`（8 行目）

`{type}`はレスポンスボディがどのようなデータを持っているかの種類が入ります。

#### `{type}`として使われる例

リクエストボディの Content-Type の例一覧と同じです。

|   Content-Type   | ファイルの種類 |
| :--------------: | :------------: |
|    text/plain    |    テキスト    |
|     text/csv     |      CSV       |
|    text/html     |      HTML      |
|     text/css     |      CSS       |
| text/javascript  |   JavaScript   |
| application/json |      JSON      |
| application/pdf  |      PDF       |
|    image/jpeg    |      JPEG      |
|    image/png     |      PNG       |
|    image/gif     |      GIF       |
|    video/mp4     |      MP4       |

### Set-Cookie: {cookies}

例：`Set-Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（9 行目）

ブラウザには cookie というブラウザ側で保存できるデータがあり、
`{cookies}`には、cookie として保存したい 値とそれに対応するキーをセットします。※1

## 備考

※1 ココら辺の話は、別のページで詳しくやります。

## 参考

ステータスコードについては、以下のサイトを参考にしました。
https://developer.mozilla.org/ja/docs/Web/HTTP/Status
