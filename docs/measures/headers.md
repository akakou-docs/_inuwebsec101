---
layout: page
title: ヘッダの設定をセキュアにする
parent: Web アプリの守り方
nav_order: 7
permalink: /measures/headers/
---

# ヘッダの設定をセキュアにする

HTTP レスポンスヘッダには、セキュリティに関するものが多くあります。
より安全になるよう設定していきましょう。

---

## ヘッダの設定をセキュアにする

HTTP レスポンスヘッダには、セキュリティに関するものが多くあります。
より安全になるよう設定していきましょう。

## セキュリティに関するヘッダ一覧

|            名前             | 内容                                                                               | 例                                          |
| :-------------------------: | :--------------------------------------------------------------------------------- | :------------------------------------------ |
|   Content Security Policy   | 別のドメインからの、ファイルの読み込みの許可等の設定を指定する                     | Content-Security-Policy: default-src 'self' |
|                             |
|  Strict-Transport-Security  | HTTP でなく、HTTPS の通信を強制できる                                              | Strict-Transport-Security: max-age=3600     |
|       X-Frame-Options       | ブラウザがそのページを `<frame>`、`<iframe>`、`<object>`で利用していいかを設定する | X-Frame-Options: deny                       |
|                             |
|      X-XSS-Protection       | ブラウザが XSS を検知して、ブロックをするかを決めるもの                            | X-XSS-Protection: 1; mode=block             |
| Access-Control-Allow-Origin | 別のサイトからのアクセスを許可するかを決めるもの                                   | Access-Control-Allow-Origin: &lt;origin&gt; |
