---
description: イベントシリアル化は処理ルールではサポートされていません。 モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコール時に直接設定する必要があります。
seo-description: イベントシリアル化は処理ルールではサポートされていません。 モバイルSDKでは、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバーコール時に直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# イベントのシリアル化{#event-serialization}

イベントシリアル化は処理ルールではサポートされていません。 モバイルSDKでは、コンテキストデータパラメーターで特殊な構文を使用して、シリアル化されたイベントをサーバーコールで直接設定する必要があります。

```js
cdata["&&events"] = "event1:12341234";
```

以下に例を示します。

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

