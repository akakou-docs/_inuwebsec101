---
layout: page
title: プレースホルダ
parent: Web アプリの守り方
nav_order: 3
permalink: /measures/placeholder/
---

# プレースホルダ

対象の脆弱性：SQL インジェクション

ハッカーは Web アプリケーションに対して、不正なパラメータを送信し、攻撃を行います。  
攻撃にはデータベースとの通信部に対して、攻撃を行うものがあります。
それらの攻撃に特に有効なのがプレースホルダです。

---

## プレースホルダとは

プレースホルダを利用すると、SQL 文を安全に組みてることができます。
SQL の構造をパラメータの値を分けて扱うことで、SQL インジェクション攻撃を防ぎます。※

ユーザの入力が SQL 文に含まれるときは、プレースホルダを利用しましょう。

## 実装例

### 危険な例

ユーザの入力を文字列を用意した文字列と連結させ、SQL 文を生成させています。これは危険なことです。

```php
/**
 * userのID（これは記載外でユーザが入力するものとする）から
 * userのnameを取り出すSQLを生成するコード
 * user_id： ユーザのID
 **/

// 文字列の連結によってSQL文を生成している。
$sql = "SELECT name FROM users WHERE id = '" . $user_id . "'";
$count = $pdo->exec($sql);
```

### プレースホルダを利用した例

SQL の構造を定義下後にパラメータを与えることで、SQL 文を安全に組みたてています。

```php
/**
 * userのID（これは記載外でユーザが入力するものとする）から
 * userのnameを取り出すSQLを生成するコード
 * user_id： ユーザのID
 **/
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = ?');

$stmt->bindValue($user_id ,$price,PDO::PARAM_INT);
$stmt->execute();
```
