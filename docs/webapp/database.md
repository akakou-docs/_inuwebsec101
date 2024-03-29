---
layout: page
title: データベース
parent: Web アプリの仕組み
nav_order: 7
permalink: /webapp/database/
---

# データベース

前提ページ：なし  
推奨ページ：[クライアントサーバモデル](../client-server-model/)

Web アプリケーションでデータを保存するときに、データベースを利用することが多くあります。

---

## データベース

Web アプリケーションでデータを保存するときに、データベースを利用することが多くあります。
データベースとは、データの保存・検索等を行うものです。

![]({{ '/assets/images/db.png' | relative_url }})

## RDB（リレーショナルデータベース）

データを表のように扱うデータベースです。
現在多くの Web アプリケーションで、RDB が用いられています。

### テーブル

データを置く表のことです。

### レコード

テーブルに置かれた各行ことを指します。
行はいくつかのデータを持ちます。

### カラム

データの属性です（ID、名前、性別等々）。

### RDB の例

#### テーブルの例 1

|  カラム 1  |  カラム 2  |  カラム 3  |  カラム 4  |
| :--------: | :--------: | :--------: | :--------: |
| データ 1_1 | データ 1_2 | データ 1_3 | データ 1_4 |
| データ 2_1 | データ 2_2 | データ 2_3 | データ 2_4 |
| データ 3_1 | データ 3_2 | データ 3_3 | データ 3_4 |

```
レコード1 = {データ1_1, データ1_2, データ1_3, データ1_4}
レコード2 = {データ2_1, データ2_2, データ2_3, データ2_4}
レコード3 = {データ3_1, データ3_2, データ3_3, データ3_4}
```

#### テーブルの例 2

| ID  | 名前  | 性別 | 年齢 |
| :-: | :---: | :--: | :--: |
|  1  |  inu  | オス |  10  |
|  2  | neko  | メス |  8   |
|  3  | usagi | オス |  2   |

```
レコード1 = {1, inu, オス, 10}
レコード2 = {2, neko, メス, 8}
レコード3 = {3, usagi, オス, 3}
```

## SQL

データベース上でデータを操作するとき、SQL という言語を利用します。　※1

## RDBMS（リレーショナルデータベース マネジメントシステム）

RDB の構築・利用・SQL の提供などの環境を提供するシステムのことです。
例としては、MySQL・PostgreSQL・SQLite などが挙げられます。

## 備考

※1 SQL に関しては、[SQL](../sql/)で説明します。
