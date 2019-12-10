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

---

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

SELECT は `テーブル名` と`カラム名` 指定したテーブルのカラムのうち、レコードが`条件`に満たすものを取得します。※1

```sql
SELECT カラム名1, カラム名2, カラム名3, ...  FROM テーブル名 WHERE 条件;
```

以下のような SQL を送信することで、`id` が 1 であるレコードの`name`をとってくることができます。
例のテーブルの場合、`inu`がデータベースから返ってきます。

```sql
SELECT name FROM users WHERE id=1;
```

### INSERT（レコードの追加）

INSERT は `テーブル名`のテーブルに、値 1, 値 2, 値 3, ...のレコードを追加します。※1

```sql
INSERT INTO テーブル名 VALUES (値1, 値2, 値3, ...);
```

以下のような SQL を送信することで、`id` が 4 で、`name`が`tora`、`email`が`tora@example.com`、`sex`が`メス`、`age`が`14`のレコードを追加することができます。

```sql
INSERT INTO users VALUES (4, "tora", "tora@example.com", "メス", 14);
```

#### 実行後のテーブル

| id  | name  |       email       | sex  | yaers |
| :-: | :---: | :---------------: | :--: | :---: |
|  1  |  inu  |  inu@example.com  | オス |  10   |
|  2  | neko  | neko@example.com  | メス |   8   |
|  3  | usagi | usagi@example.com | オス |   2   |
|  4  | tora  | tora@example.com  | メス |  14   |

### UPDATE（レコードの更新）

UPDATE は `テーブル名`のテーブルの`条件`を満たすレコードに、`変更`に指定した変更を加えます。※1

```sql
UPDATE テーブル名 SET 変更 WHERE 条件;
```

以下のような SQL を送信することで、`id`が 1 であるデータの`age`を 19 に変更できます。

```sql
UPDATE users SET age=19 WHERE id=1;
```

#### 実行後のテーブル

| id  | name  |       email       | sex  | yaers |
| :-: | :---: | :---------------: | :--: | :---: |
|  1  |  inu  |  inu@example.com  | オス |  19   |
|  2  | neko  | neko@example.com  | メス |   8   |
|  3  | usagi | usagi@example.com | オス |   2   |

### DELETE（レコードの消去）

DELETE は `テーブル名`のテーブルの`条件`を満たすレコードを消去します。※1

```
DELETE FROM テーブル名　WHERE 条件;
```

以下のような SQL を送信することで、`id`が 1 であるレコードを消去することができます。

```sql
DELETE FROM users　WHERE id=1;
```

#### 実行後のテーブル

| id  | name  |       email       | sex  | age |
| :-: | :---: | :---------------: | :--: | :-: |
|  2  | neko  | neko@example.com  | メス |  8  |
|  3  | usagi | usagi@example.com | オス |  2  |

## 備考

※1 厳密な説明ではありませんが、今回は SQL の概要を知ってもらうことを目的としているので、言及しません。
