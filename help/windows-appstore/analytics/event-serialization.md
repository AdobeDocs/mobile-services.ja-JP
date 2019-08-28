---
description: イベントのシリアル化は処理ルールでサポートされていません。モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
seo-description: イベントのシリアル化は処理ルールでサポートされていません。モバイル SDK では、コンテキストデータパラメーター内で特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Marketing Cloud、Analytics
title: イベントのシリアル化
topic: 開発者と導入
uuid: a5966d05- e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# Event serialization{#event-serialization}

イベントのシリアル化は処理ルールでサポートされていません。モバイルSDKでは、コンテキストデータパラメーターで特別な構文を使用して、シリアル化されたイベントをサーバーコールで直接設定する必要があります。

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

