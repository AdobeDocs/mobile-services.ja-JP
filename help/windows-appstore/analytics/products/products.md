---
description: products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。
solution: Experience Cloud Services,Analytics
title: products 変数
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# products 変数{#products-variable}

products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。

次の手順で *`products`* 変数を使用する場合は、コンテキストデータキーをに設定します。 `"&&products"`を設定し、 *`products`*:

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

*`products`* は画像リクエストに直接設定され、その他の変数はコンテキストデータとして設定されることに注意してください。すべてのコンテキストデータ変数は、処理ルールを使用してマッピングする必要があります。

![](assets/products-procrules.png)

この *`products`* 変数をマッピングする必要はありません。画像リクエストに直接設定されるからです。
