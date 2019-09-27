---
description: products 変数は、処理ルールを使用して設定することができません。モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、products をサーバー呼び出しで直接設定する必要があります。
seo-description: products 変数は、処理ルールを使用して設定することができません。モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、products をサーバー呼び出しで直接設定する必要があります。
seo-title: 製品変数
solution: Marketing Cloud,Analytics
title: 製品変数
topic: 開発者と導入
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

products 変数は、処理ルールを使用して設定することができません。モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、products をサーバー呼び出しで直接設定する必要があります。

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products` variable:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

以下に例を示します。

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

The *`products`* is set directly on the image request, and the other variables are set as context data. すべてのコンテキストデータ変数は、処理ルールを使用してマッピングする必要があります。

![](assets/products-procrules.png)

処理ルールを使用して変数をマッピ *`products`* ングする必要はありません。これは、SDKがイメージリクエストに直接設定するためです。

## Products variable with merchandising eVars and product-specific events {#section_685D53AD3D064F9A8E225F995A9BA545}

An example of the *`products`* variable with Merchandising eVars and product-specific events.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>変数を使用して製品固有のイベントをトリガーする場合は、そのイベントを変数に設定する必要もあります。設定しない場 *`&&products`**`&&events`* 合は、処理中にそのイベントが除外されます。

