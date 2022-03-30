---
description: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数の例を以下に示します。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud Services,Analytics
title: マーチャンダイジング eVar および製品固有のイベントを持つ products 変数
topic-fix: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
exl-id: 2ede6341-3068-4423-a509-c0ec3a2db5e8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# マーチャンダイジング eVar および製品固有のイベントを持つ products 変数 {#products-variable-with-merchandising-evars-and-product-specific-events}

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
>変数を使用して製品固有のイベントをトリガーする場合は、*`&&products`* 変数を使用して製品固有のイベントをトリガーする場合は、*`&&events`* 変数でもイベントを設定する必要があります。設定しなかった場合、そのイベントは処理中に除外されます。
