---
description: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。
keywords: android;library;mobile;sdk
seo-description: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。
seo-title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
solution: Marketing Cloud,Analytics
title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
topic: 開発者と導入
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>If you trigger a product-specific event by using the  variable, you must also set that event in the  variable. *`&&products`**`&&events`*&#x200B;設定しなかった場合、そのイベントは処理中に除外されます。

