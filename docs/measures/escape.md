---
layout: page
title: エスケープ
parent: Web アプリの守り方
nav_order: 1
permalink: /measures/escape/
---

# エスケープ（無害化）

対象の脆弱性：いろんなもの

ハッカーは Web アプリケーションに対して、不正なパラメータを送信し、攻撃を行います。  
これらの攻撃から、身を守る手段の一つがエスケープです。

---

## エスケープ

入力を無害なデータに変換して出力することです。
ハッカーが攻撃に利用するデータは特殊な文字（プログラム上意味を持つ文字）を含んでいることが多くあり、エスケープではその特殊な文字を無害な文字列に変換します。

## HTML の場合

HTML をエスケープしない場合、XSS（クロスサイトスクリプティング）の攻撃が行われてしまう可能性があります。

### 攻撃に利用される特殊な文字の例

例えば、以下のような文字には気をつけなければいけません。

```
'';"<>&
```

### PHP のコード

以下のコードでは、`htmlspecialchars($name, ENT_QUOTES)`で`$name`をエスケープしています。

```php
<p><?php
$name = $_GET['name'];
$escaped_name = htmlspecialchars($name, ENT_QUOTES);
echo $escaped_name;
?></p>
```

### PHP が生成したコード

`name` に危険そうなデータを入れると、無害化されて返ってきます。  
以下では`'';"<>&`を`name`に追加しています。

```html
<p>&#039;&#039;;&quot;&lt;&gt;&amp;</p>
```
