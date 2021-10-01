---
description: products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。
solution: Experience Cloud,Analytics
title: products 変数
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# products 変数{#products-variable}

products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。

*`products`* 変数を設定するには、コンテキストデータキーを `"&&products"` に設定し、*`products`* 用に定義された構文を使用して値を設定します。

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

*`products`* 変数は SDK によってイメージリクエストに直接設定されるので、処理ルールを使用してマッピングする必要はありません。
