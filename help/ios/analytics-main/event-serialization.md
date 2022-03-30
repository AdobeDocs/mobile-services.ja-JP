---
description: 処理ルールではイベントのシリアル化はサポートされていません。Mobile SDK では、コンテキストデータパラメーターで特殊な構文を使用して、サーバーコールでシリアル化されたイベントを直接設定する必要があります。
solution: Experience Cloud Services,Analytics
title: イベントのシリアル化
topic-fix: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
exl-id: c34331a4-bfe2-4955-807b-92a3303f8d81
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '70'
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
