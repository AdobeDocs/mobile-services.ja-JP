---
description: products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。
seo-description: products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。
seo-title: products 変数
solution: Experience Cloud,Analytics
title: products 変数
topic-fix: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
exl-id: 0575236c-9858-4bf9-a2ce-6e2667d58ddd
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

---

# products 変数 {#products-variable}

products変数は処理ルールを使用して設定できません。 モバイルSDKでは、コンテキストデータパラメーター内で特別な構文を使用して、サーバーコール時に製品を直接設定する必要があります。

*`products`*&#x200B;変数を設定するには、コンテキストデータキーを`"&&products"`に設定し、*`products`変数に定義された構文を使用して値を設定します。

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

次に例を示します。

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

*`products`*&#x200B;はイメージリクエスト上で直接設定され、他の変数はコンテキストデータとして設定されます。 すべてのコンテキストデータ変数は、次の処理ルールを使用してマッピングする必要があります。

![](assets/products-procrules.png)

処理ルールを使用して&#x200B;*`products`*&#x200B;変数をマッピングする必要はありません。これは、変数がSDKのイメージリクエストに直接設定されるからです。

## マーチャンダイジング eVar および製品固有のイベントを持つ products 変数 {#section_685D53AD3D064F9A8E225F995A9BA545}

*`products`*&#x200B;変数とマーチャンダイジングeVarおよび製品固有のイベントの例です。

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
>*`&&products`*&#x200B;変数を使用して製品固有のイベントをトリガーする場合は、そのイベントを&#x200B;*`&&events`*&#x200B;変数に設定する必要もあります。設定しない場合、イベントは処理中に除外されます。
