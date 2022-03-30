---
description: products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。
solution: Experience Cloud Services,Analytics
title: products 変数
topic-fix: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
exl-id: 0575236c-9858-4bf9-a2ce-6e2667d58ddd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 7%

---

# products 変数 {#products-variable}

products 変数は、処理ルールを使用して設定することはできません。 モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、サーバー呼び出しで直接製品を設定する必要があります。

次の手順で *`products`* 変数を使用する場合は、コンテキストデータキーをに設定します。 `"&&products"`を設定し、 *`products` 変数：

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

例：

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

この *`products`* はイメージリクエストに直接設定され、その他の変数はコンテキストデータとして設定されます。 すべてのコンテキストデータ変数は、処理ルールを使用してマッピングする必要があります。

![](assets/products-procrules.png)

この *`products`* 変数をマッピングする必要はありません。画像リクエストに直接設定されるからです。

## マーチャンダイジング eVar および製品固有のイベントを持つ products 変数 {#section_685D53AD3D064F9A8E225F995A9BA545}

例 *`products`* 変数にマーチャンダイジング eVar および製品固有のイベントを格納する必要があります。

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
>製品固有のイベントをトリガーする場合、 *`&&products`* 変数を使用する場合は、そのイベントを *`&&events`* 変数に含める必要はありません。それ以外の場合は、処理中にイベントが除外されます。
