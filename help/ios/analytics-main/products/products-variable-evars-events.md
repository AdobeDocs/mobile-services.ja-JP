---
description: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。
seo-description: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。
seo-title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
solution: Marketing Cloud,Analytics
title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
topic: 開発者と導入
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>変数を使用して製品固有のイベントをトリガーする場合は、 *`&&products`* そのイベントを変数に設定する必要もあり *`&&events`* ます。 設定しなかった場合、そのイベントは処理中に除外されます。

