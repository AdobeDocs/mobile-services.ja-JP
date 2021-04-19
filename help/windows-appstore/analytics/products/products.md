---
description: products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。
seo-description: products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。
seo-title: products 変数
solution: Experience Cloud,Analytics
title: products 変数
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 13%

---

# products 変数 {#products-variable}

products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。

*`products`*&#x200B;変数を設定するには、コンテキストデータキーを`"&&products"`に設定し、*`products`*&#x200B;に定義された構文を使用して値を設定します。

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

*`products`* は画像リクエストに直接設定され、その他の変数はコンテキストデータとして設定されることに注意してください。すべてのコンテキストデータ変数は、次の処理ルールを使用してマッピングする必要があります。

![](assets/products-procrules.png)

処理ルールを使用して&#x200B;*`products`*&#x200B;変数をマッピングする必要はありません。これは、変数がSDKのイメージリクエストに直接設定されるからです。
