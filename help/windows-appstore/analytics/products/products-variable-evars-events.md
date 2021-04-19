---
description: マーチャンダイジングeVarおよび製品固有のイベントを含むproducts変数の例を示します。
seo-description: マーチャンダイジングeVarおよび製品固有のイベントを含むproducts変数の例を示します。
seo-title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
solution: Experience Cloud,Analytics
title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
topic-fix: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
exl-id: 3a90f624-da13-4c26-9e4c-3a4af33bc5ee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---

# マーチャンダイジング eVar および製品固有のイベントを持つ products 変数{#products-variable-with-merchandising-evars-and-product-specific-events}

マーチャンダイジングeVarおよび製品固有のイベントを含むproducts変数の例を示します。

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
