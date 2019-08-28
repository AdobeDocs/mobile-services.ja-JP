---
description: products 変数をマーチャンダイジング eVar および製品固有イベントと共に使用した例です。
seo-description: products 変数をマーチャンダイジング eVar および製品固有イベントと共に使用した例です。
seo-title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
solution: Marketing Cloud、Analytics
title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
topic: 開発者と導入
uuid: 94e882e4- b19d-4c48-9dfb-331465490347
translation-type: tm+mt
source-git-commit: b630c5cf09be7fbe31018cbf50564001eb6e2a5a

---


# Products variable with merchandising eVars and product-specific events{#products-variable-with-merchandising-evars-and-product-specific-events}

products 変数をマーチャンダイジング eVar および製品固有イベントと共に使用した例です。

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
>*`&&products`* 変数を使用して製品固有のイベントをトリガーする場合、そのイベントを *`&&events`* 変数に設定する必要もあります。そうしないと、処理中にイベントが除外されます。

