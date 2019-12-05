---
layout: page
title: Cookie
parent: Webアプリケーションの仕組み
nav_order: 6
permalink: /webapp/cookie/
---

# Cookie

前提ページ：[クライアントサーバモデル](../client-server-model/)  
推奨ページ：[ウェブページの仕組み](../webpage/)

Webアプリケーションを作成するときに、ブラウザ側でデータを保存したいことがあります。
それを叶えるのが、cookieです。

## cookieとは

ブラウザにデータを保存させる仕組みです。
またこの保存されたデータもcookieと呼びます。


### cookieに関わるHTTPヘッダ

#### Cookie: {cookies}

例：`Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（10 行目）

`Cookie`はクライアントが持っているCookieを、サーバに提供するためのヘッダです。  
`{cookies}`は複数の cookie（データとそれに対応するキー）を持ちます。 

#### Set-Cookie {cookies}

例：`Set-Cookie: _ga=GA1.1.11882848.1574929583; _ga_J5E5G995V7=GS1.1.1574933002.2.1.1574936118.0`（9 行目）

`Cookie`はクライアント持つCookieを、サーバ側が指定するためのヘッダです。  
`{cookies}`には、cookie として保存したい 値とそれに対応するキーをセットします。

