---
description: Adobe Mobile iOS SDK を使用することで、モバイルアプリ内のディープリンクおよびディファードディープリンクを追跡できます。
solution: Experience Cloud,Analytics
title: ディープリンクの追跡
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
exl-id: a8b20233-d800-4318-ad4f-39229d8b3a5e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# ディープリンクの追跡{#tracking-deep-links}

Adobe Mobile iOS SDK を使用することで、モバイルアプリ内のディープリンクおよびディファードディープリンクを追跡できます。

マーケターがアプリケーションでディープリンクを使用する方法について詳しくは、 Mobile Services ドキュメントの[獲得](/help/ios/acquisition-main/acquisition.md)を参照してください。

## ディープリンクの追跡

1. SDK をプロジェクトに追加し、ライフサイクル指標を実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. アプリ間通信の処理またはユニバーサルリンクのサポートのためにアプリケーションを登録します。

   詳しくは、「[アプリ間通信](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10)」または「[ユニバーサルリンクのサポート](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)」を参照してください。

1. openURL でディープリンクを追跡します。

   以下に、ディープリンクの追跡例を示します。

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

Adobe Mobile SDK は、任意のディープリンクまたはユニバーサルリンクに `a.deeplink.id` というラベルを持つキーと、対応する null 以外のユーザー生成値が含まれる場合、そのリンクに追加されたデータのキーと値のペアを解析できます。リンクに `a.deeplink.id` キーと値が含まれる場合、そのリンクに追加されたデータのすべてのキーと値のペアが解析され、ライフサイクルヒットに添付されて、Adobe Analytics に送信されます。

以下の 1 つ以上の予約済みキー（とユーザー生成値）をディープリンクまたはユニバーサルリンクに追加することもできます。

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

これらのキーは、Adobe Analytics でのレポート用にあらかじめマッピングされている変数です。マッピングと処理ルールについて詳しくは、「[処理ルールとコンテキストデータ](/help/ios/getting-started/proc-rules.md)」を参照してください。

### ディファードディープリンクの追跡

1. AdobeDataCallback を登録します。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. `AdobeDataCallback` 内で `ADBMobileDataEventDeepLink` を処理します。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## ディープリンク公開情報 {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### メソッド

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### 定数

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```
