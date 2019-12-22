---
layout: page
title: CSRF トークン
parent: Web アプリの守り方
nav_order: 4
permalink: /measures/csrf-token/
---

# CSRF トークン

ハッカーは CSRF の脆弱性をついて、攻撃をしてくることがあります。
今回はその対策に関する話です。

対象：CSRF

---

## CSRF トークン

CSRF（クロスサイトリクエストフォージェリ）という攻撃・脆弱性があります。
これを解決する手段が CSRF トークンの利用です。

## フレームワーク・ライブラリ

CSRF トークンの生成等を機能としても持つ、フレームワークやライブラリが存在します。それを利用しましょう。
