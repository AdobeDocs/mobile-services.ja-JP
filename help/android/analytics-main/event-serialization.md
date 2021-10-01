---
description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '74'
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
