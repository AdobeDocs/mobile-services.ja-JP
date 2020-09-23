---
description: products変数は、処理ルールを使用して設定することはできません。 iOS 4.x SDKでは、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールで直接製品を設定する必要があります。
seo-description: products変数は、処理ルールを使用して設定することはできません。 iOS 4.x SDKでは、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールで直接製品を設定する必要があります。
seo-title: products 変数
solution: Experience Cloud,Analytics
title: products 変数
topic: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 44%

---


# products 変数{#products-variable}

products変数は、処理ルールを使用して設定することはできません。 iOS 4.x SDKでは、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールで直接製品を設定する必要があります。

*`products`* 変数を設定するには、コンテキストデータキーを `"&&products"` に設定し、*`products`* 変数用に定義された構文を使用して値を設定します。

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

以下に例を示します。

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* は画像リクエストに直接設定され、その他の変数はコンテキストデータとして設定されることに注意してください。すべてのコンテキストデータ変数は、処理ルールを使用してマッピングする必要があります。

![](assets/map-products.png)

処理ルールを使用して&#x200B;*`products`*&#x200B;変数をマッピングする必要はありません。画像リクエストに直接設定されるからです。
