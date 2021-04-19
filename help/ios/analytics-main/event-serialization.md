---
description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
seo-description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
seo-title: イベントのシリアル化
solution: Experience Cloud,Analytics
title: イベントのシリアル化
topic-fix: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
exl-id: c34331a4-bfe2-4955-807b-92a3303f8d81
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
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
