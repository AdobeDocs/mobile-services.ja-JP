---
description: Adobe Mobile iOS SDK を使用することで、モバイルアプリ内のディープリンクおよびディファードディープリンクを追跡できます。
seo-description: Adobe Mobile iOS SDK を使用することで、モバイルアプリ内のディープリンクおよびディファードディープリンクを追跡できます。
seo-title: ディープリンクの追跡
solution: Marketing Cloud,Analytics
title: ディープリンクの追跡
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links{#tracking-deep-links}

Adobe Mobile iOS SDK を使用することで、モバイルアプリ内のディープリンクおよびディファードディープリンクを追跡できます。

マーケターがアプリケーションでディープリンクを使用する方法について詳しくは、 Mobile Services ドキュメントの[獲得](/help/ios/acquisition-main/acquisition.md)を参照してください。

## ディープリンクの追跡

1. SDK をプロジェクトに追加し、ライフサイクル指標を実装します。

   詳しくは、コア実装とラ *イフサイクルでのプロジェクトへのSDKと設定ファイルの追加* ( [英語のみ)を参照してください](/help/ios/getting-started/dev-qs.md)。
1. アプリケーションを登録して、アプリケーション間の通信を処理するか、ユニバーサルリンクをサポートします。

   詳しくは、「アプリ間通信 [」または「ユニバーサルリンクのサポ](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10)[ート」を参照してください](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

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

The Adobe Mobile SDK can parse key and value pairs of data appended to any deep or Universal Link, provided that the link contains a key with a `a.deeplink.id` label and a corresponding non-null and user generated value. リンクに `a.deeplink.id` キーと値が含まれる場合、そのリンクに追加されたデータのすべてのキーと値のペアが解析され、ライフサイクルヒットに添付されて、Adobe Analytics に送信されます。

You might also choose to append one or more of the following reserved keys (with user-generated values) to the deep or Universal Link:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

これらのキーは、Adobe Analytics でのレポート用にあらかじめマッピングされている変数です。マッピングと処理ルールについて詳しくは、[処理ルールとコンテキストデータ](/help/ios/getting-started/proc-rules.md)を参照してください。

### 遅延ディープリンクの追跡

1. AdobeDataCallback を登録します。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. 中の `ADBMobileDataEventDeepLink` ハンドル `AdobeDataCallback`。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Deep link public information {#section_44600E9AA68D4A53AA0C14BD86CC5284}

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

