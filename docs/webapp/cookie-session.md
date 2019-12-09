---
layout: page
title: Cookieとセッション
parent: Webアプリケーションの仕組み
nav_order: 6
permalink: /webapp/cookie-session/
---

# Cookieとセッション

前提ページ：[クライアントサーバモデル](../client-server-model/)  
推奨ページ：[ウェブページの仕組み](../webpage/)

Webアプリケーションを作成するときに、ブラウザ側でデータを保存したいことがあります。
それを叶えるのが、cookieです。

## Cookie

ブラウザにデータを保存させる仕組みです。
またこの保存されたデータもCookieと呼びます。

### Cookieに関わるHTTPヘッダ

#### Cookie: {cookies}

例：`Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（10 行目）

`Cookie`はクライアントが持っているCookieを、サーバに提供するためのヘッダです。  
`{cookies}`は複数の cookie（データとそれに対応するキー）を持ちます。 

#### Set-Cookie {cookies}

例：`Set-Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（9 行目）

`Cookie`はクライアント持つCookieを、サーバ側が指定するためのヘッダです。  
`{cookies}`には、cookie として保存したい 値とそれに対応するキーをセットします。


### Cookie利用の流れ

#### 1. Cookieを取得

ブラウザがサーバにHTTPリクエストを送信し，
サーバが `Set-Cookie` を含むHTTPレスポンスを返します。

ブラウザーはこの `Set-Cookie` の値を保存します。

![]({{ '/assets/images/cookie1.png' | relative_url }})

#### 2.　Cookieの送信

ブラウザが保存したcookieを取り出し、サーバに`Cookie` ヘッダに付与して、HTTPリクエストを送信します。

![]({{ '/assets/images/cookie2.png' | relative_url }})


## Cookieを利用したセッション

サーバがクライアントが誰であるかを認識する仕組みをセッションといいます。
多くの場合cookieにセッションIDと呼ばれる、IDを付加することで個人を認識します。

### Cookie利用の流れ

画像のセッションIDは、本来より短くなっていますが、もっと長い強固なIDを利用してください。

#### 1. セッションIDをふる

サーバはユーザのレスポンスに生成したセッションIDを渡します。
このセッションIDの生成には、十分なランダム性と長さが必要です。 ※1

![]({{ '/assets/images/session1.png' | relative_url }})

#### 2. セッションIDを利用する

二回目以降のリクエストからは、セッションIDの値から、サーバはユーザを特定します。
この例の場合、事前に保存していたセッションIDとユーザの名前が対応するデータから、ユーザ名を取り出しています。

![]({{ '/assets/images/session2.png' | relative_url }})

## 備考

※1 HTTPは状態を持たないので、このようなことが置きます。これを「HTTPはステートレスである」といいます。  
※2 セッションIDが脆弱だとなりすましが行われます。