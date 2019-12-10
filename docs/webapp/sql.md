---
layout: page
title: SQL
parent: Webアプリケーションの仕組み
nav_order: 8
permalink: /webapp/sql/
---

# データベース

前提ページ：[データベース](../database/)  
推奨ページ：なし

Web アプリケーションでデータを保存するときに、データベースを利用することが多くあります。
今回はその操作を行うのに必要な SQL を学びます。

別章の説明では、SELECT 文のみ利用します。

## SQL

SQL とは、データベースに操作を伝えるための言語です。
SQL には様々な種類がありますが、今回は MySQL という RDBMS の SQL を利用します。

## 操作

### テーブルの例

以下のようなテーブルを`users` として置いて、各 SQL の操作について説明します。

| id  | name  |       email       | sex  | age |
| :-: | :---: | :---------------: | :--: | :-: |
|  1  |  inu  |  inu@example.com  | オス | 10  |
|  2  | neko  | neko@example.com  | メス |  8  |
|  3  | usagi | usagi@example.com | オス |  2  |

### SELECT (レコードの取得)

```sql
SELECT カラム名1, カラム名2, カラム名3, ...  FROM テーブル名 WHERE 条件;
```

以下のような SQL を送信することで、`id` が 1 であるレコードの`name`をとってくることができます。
例のテーブルの場合、`inu`がデータベースから返ってきます。

```sql
SELECT name FROM users WHERE id=1;
```

### INSERT（レコードの追加）

```sql
INSERT INTO テーブル名 values (値1, 値2, 値3, ...);
```

以下のような SQL を送信することで、`id` が 4 で、`name`が`tora`、`email`が`tora@example.com`、`sex`が`メス`、`age`が`14`のレコードを追加することができます。

```sql
INSERT INTO users values (4, "tora", "tora@example.com", "メス", 14);
```

#### 実行後のテーブル

| id  | name  |       email       | sex  | yaers |
| :-: | :---: | :---------------: | :--: | :---: |
|  1  |  inu  |  inu@example.com  | オス |  10   |
|  2  | neko  | neko@example.com  | メス |   8   |
|  3  | usagi | usagi@example.com | オス |   2   |
|  4  | tora  | tora@example.com  | メス |  14   |

## 備考
