---
layout: page
title: バリデーションチェック
parent: 危険なパラメータから守る
nav_order: 1
permalink: /measures/parameters/validation/
---

# バリデーションチェック

ハッカーは Web アプリケーションに対して、不正なパラメータを送信し、攻撃を行います。  
この不正なパラメータは我々の想定した値域、長さ、形式など外れたコードが飛んでくることがあります。

対象：いろんなモノ

---

## バリデーションチェック

入力が正しいかを確認することをバリデーションチェックといいます。
どんなパラメータの値が送られてきたとしてもサーバが想定外の動きをしないよう、危険・想定外の入力はバリデーションチェックで弾きます。

## 値域のチェック

以下では入力値の数値を検証しています。

```php
<p>
<?php
// リクエストパラメータにからageを取得
$age_string = $_GET['age'];

// age_stringが数値を表す文字列以外なら終了
if (!ctype_digit($age_string)) exit(1);

// age_stringを数値に変換して、ageに代入
$age = intval($age_string);

// ageが0未満なら終了
if ($age < 0) exit(1);

// ageが200より大きいなら終了
if ($age > 200) exit(1);

echo $age;
?>
</p>
```
