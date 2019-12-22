---
layout: page
title: Cookieの設定
parent: Web アプリの守り方
nav_order: 6
permalink: /measures/cookie-setting/
---

# Cookie の設定

前提知識：[Cookie とセッション](../../webapp/cookie-session/)  
対象の脆弱性：XSS（リスク軽減）

Cookie はセッション ID を持つことがあるので、盗まれてしまうとかなり不味いです。
Cookie に対する設定で、漏洩のリスクが下げられることがあります。

---

## Cookie の設定

Cookie はセッション ID を持つことがあるので、盗まれてしまうとかなり不味いです。
Cookie に対する設定で、漏洩のリスクが下げられることがあります。

## 設定項目一覧

|   名前   | 意味                                                                      |               例               |
| :------: | :------------------------------------------------------------------------ | :----------------------------: |
|  domain  | Cookie を送信するドメイン                                                 |          example.com           |
|   path   | Cookie を送信する URI（の一番ルート）                                     |           /index.php           |
| max-age  | Cookie の寿命（秒）                                                       |              3600              |
|  expire  | 有効期限が切れる日付                                                      | Fri, 31-Dec-1999 23:59:59 GMT; |
|  secure  | この属性が true の場合、http 通信の場合 cookie は送られなくなる。         |             false              |
| httponly | この属性が true の場合、JavaScript が Cookie にアクセスできないようになる |             false              |
