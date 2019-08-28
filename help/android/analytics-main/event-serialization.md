---
description: イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
keywords: android;library;mobile;sdk
seo-description: イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Marketing Cloud、Analytics
title: イベントのシリアル化
topic: 開発者と導入
uuid: acdeda16- ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Event serialization {#event-serialization}

イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。

```java
cdata.put("&&events", "event1:12341234");
```

以下に例を示します。

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

