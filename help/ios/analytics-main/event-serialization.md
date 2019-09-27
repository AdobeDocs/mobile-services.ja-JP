---
description: イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
seo-description: イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Marketing Cloud,Analytics
title: イベントのシリアル化
topic: 開発者と導入
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Event serialization {#event-serialization}

イベントのシリアル化は処理ルールでサポートされていません。Mobile SDK では、コンテキストデータパラメーターに特殊な構文を使用して、シリアル化されたイベントをサーバー呼び出しで直接設定する必要があります。

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

以下に例を示します。

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

