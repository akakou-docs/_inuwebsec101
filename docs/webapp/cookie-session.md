---
layout: page
title: Cookieとセッション
parent: Web アプリの仕組み
nav_order: 6
permalink: /webapp/cookie-session/
---

# Cookie とセッション

前提ページ：[クライアントサーバモデル](../client-server-model/)  
推奨ページ：[ウェブページの仕組み](../webpage/)

Web アプリケーションを作成するときに、ブラウザ側でデータを保存したいことがあります。
それを叶えるのが、cookie です。

---

## Cookie

ブラウザにデータを保存させる仕組みです。
またこの保存されたデータも Cookie と呼びます。

### Cookie に関わる HTTP ヘッダ

#### Cookie: {cookies}

例：`Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（10 行目）

`Cookie`はクライアントが持っている Cookie を、サーバに提供するためのヘッダです。  
`{cookies}`は複数の cookie（データとそれに対応するキー）を持ちます。

#### Set-Cookie {cookies}

例：`Set-Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（9 行目）

`Cookie`はクライアント持つ Cookie を、サーバ側が指定するためのヘッダです。  
`{cookies}`には、cookie として保存したい 値とそれに対応するキーをセットします。

### Cookie 利用の流れ

#### 1. Cookie を取得

ブラウザがサーバに HTTP リクエストを送信し，
サーバが `Set-Cookie` を含む HTTP レスポンスを返します。

ブラウザーはこの `Set-Cookie` の値を保存します。

![]({{ '/assets/images/cookie1.png' | relative_url }})

#### 2.　 Cookie の送信

ブラウザが保存した cookie を取り出し、サーバに`Cookie` ヘッダに付与して、HTTP リクエストを送信します。

![]({{ '/assets/images/cookie2.png' | relative_url }})

## Cookie を利用したセッション

サーバがクライアントが誰であるかを認識する仕組みをセッションといいます。
多くの場合 cookie にセッション ID と呼ばれる、ID を付加することで個人を認識します。

### Cookie 利用の流れ

画像のセッション ID は、本来より短くなっていますが、もっと長い強固な ID を利用してください。

#### 1. セッション ID をふる

サーバはユーザのレスポンスに生成したセッション ID を渡します。
このセッション ID の生成には、十分なランダム性と長さが必要です。 ※1

![]({{ '/assets/images/session1.png' | relative_url }})

#### 2. セッション ID を利用する

二回目以降のリクエストからは、セッション ID の値から、サーバはユーザを特定します。
この例の場合、事前に保存していたセッション ID とユーザの名前が対応するデータから、ユーザ名を取り出しています。

![]({{ '/assets/images/session2.png' | relative_url }})

## 備考

※1 HTTP は状態を持たないので、このようなことが置きます。これを「HTTP はステートレスである」といいます。  
※2 セッション ID が脆弱だとなりすましが行われます。
