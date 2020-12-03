---
description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
seo-description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 100%

---


# イベントのシリアル化 {#event-serialization}

処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。

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

