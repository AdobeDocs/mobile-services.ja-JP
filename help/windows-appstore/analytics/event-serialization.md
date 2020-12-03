---
description: 処理ルールではイベントのシリアル化はサポートされていません。モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコール時に直接設定する必要があります。
seo-description: 処理ルールではイベントのシリアル化はサポートされていません。モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコール時に直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---


# イベントのシリアル化{#event-serialization}

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

