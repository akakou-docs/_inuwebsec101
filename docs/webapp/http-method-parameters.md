---
layout: page
title: HTTPメソッドとパラメータ
parent: Webアプリケーションの仕組み
nav_order: 5
permalink: /webapp/http-method
---

# HTTP メソッドとパラメータ

前提ページ：[HTTP](../http.md)、[HTTP ヘッダ](../http-headers.md)
推奨ページ：[クライアントサーバモデル](../client-server-model/)

セキュアな Web サイトの作り方を学ぶ上で、Web サイトがどのように通信をしているかを知ることは重要です。このページでは Web 上の通信で利用される HTTP(S)のメソッドについて、学びます。

---

## HTTP メソッド

HTTP メソッドとは、アクセスしたいサーバ上のリソース（ファイル等）に対して、どのような操作をしたいのかを表すものです。

#### HTTP メソッドの有名所

| メソッド |      意味      |
| :------: | :------------: |
|   GET    | リソースの取得 |
|   POST   | リソースの追加 |
|   PUT    | リソースの更新 |
|  PATCH   | リソースの更新 |
|  DELETE  | リソースの消去 |
