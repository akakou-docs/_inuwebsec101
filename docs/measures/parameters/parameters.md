---
layout: page
title: 危険なパラメータから守る
nav_order: 1
parent: Web アプリの守り方
has_children: true
permalink: /measures/parameters/
---

# 危険なパラメータから守る

前提ページ：[HTTP メソッドとパラメータ](../../webapp/http-method/)  
推奨ページ：なし

Web アプリケーションは多くのパラメータ※を扱います。

#### パラメータの例

- リクエスト パラメータ
- POST パラメータ
- Cookie
- URI

そのパラメータに悪意のあるデータを含ませることで、攻撃者は攻撃を行います。
この章では、危険なパラメータから Web ページを守る手段について説明します。

#### 攻撃される例

![]({{ '/assets/images/hack-parameter.png' | relative_url }})

### 備考

※ Web アプリケーションがクライアントから受け取る情報を、パラメータと読んでいます。
