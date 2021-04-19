---
description: 処理ルールではイベントのシリアル化はサポートされていません。モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコールで直接設定する必要があります。
seo-description: 処理ルールではイベントのシリアル化はサポートされていません。モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコールで直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic-fix: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# イベントのシリアル化 {#event-serialization}

処理ルールではイベントのシリアル化はサポートされていません。モバイルSDKでは、コンテキストデータパラメーターで特殊な構文を使用して、シリアル化されたイベントをサーバーコールで直接設定する必要があります。

```js
cdata["&&events"] = "event1:12341234";
```

次に例を示します。

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
