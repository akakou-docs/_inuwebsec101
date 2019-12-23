---
layout: page
title: ヘッダの設定をセキュアにする
parent: Web アプリの守り方
nav_order: 7
permalink: /measures/headers/
---

# ヘッダの設定をセキュアにする

前提知識：[HTTP ヘッダ](../../webapp/http-headers)  
対象の脆弱性：いろいろ

HTTP レスポンスヘッダには、セキュリティに関するものが多くあります。
より安全になるよう設定していきましょう。

---

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

## 推奨の設定

### Content Security Policy

Content Security Policy は最低限で設定すべきです。

#### 例

```http
Content-Security-Policy: default-src 'self'
```

### Strict-Transport-Security

Strickt-Transport-Secruity は有効になるよう設定すべきです。

#### 例

```http
Strict-Transport-Security: max-age=3600
```

### X-Frame-Options

X-Frame-Options は最低限で設定すべきです。
必要がなければ、DENY または SAME ORIGIN を推奨します。

#### 例

```http
X-Frame-Options: deny
```

### X-XSS-Protection

X-XSS-Protection は有効になるよう設定すべきです。

#### 例

```http
X-XSS-Protection: 1; mode=block
```

### Access-Control-Allow-Origin

Access-Control-Allow-Origin は最低限で設定すべきです。
必要がなければ、`<origin>` または無設定を推奨します。

#### 例

```http
Access-Control-Allow-Origin: <origin>
```
