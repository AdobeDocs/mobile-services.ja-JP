---
description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
keywords: android;library;mobile;sdk
seo-description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '104'
ht-degree: 100%

---


# イベントのシリアル化 {#event-serialization}

処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。

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

