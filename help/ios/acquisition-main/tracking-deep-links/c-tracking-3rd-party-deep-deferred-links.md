---
description: iOS SDK を使用して、サードパーティのディファードディープリンクの追跡を実装します。
title: サードパーティのディファードディープリンクの追跡
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
exl-id: c6d2ec6e-cd2a-4670-96e9-cb5e09f7cc10
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 90%

---

# サードパーティのディファードディープリンクの追跡 {#tracking-third-party-deferred-deep-links}

iOS SDK を使用して、サードパーティのディファードディープリンクの追跡を実装します。

## 従来の Adobe Mobile SDK ディープリンク {#section_D114FA1EB9664EAA82E036A990694B26}

現在、Adobe Mobile SDK がサポートしているディープリンクでは、アプリ開発者が `trackAdobeDeepLink` API を呼び出し、ディープリンクの URL（設定時に Adobe Mobile Services で生成されるフィンガープリンター URL）を渡すことが求められます。SDK はフィンガープリンターに Ping を発行して、獲得データを取得し、ライフサイクルの一部としてインストール／起動分析コールのコンテキストデータに追加します。さらに、SDK は、ディープリンク URL のパラメーターからのディープリンクデータも追加します。ディープリンクについて詳しくは、[ディープリンクの追跡](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md)を参照してください。

## Facebook ディープリンク {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

広告作成者は、Facebook 上に広告をディープリンクとして作成することができます。ユーザーが Facebook 上の広告をクリックすると、アプリに興味を持った情報に直接移動します。ディープリンクはフィンガープリンターの URL では&#x200B;**ありません**。ただし、広告の設定時にサードパーティのディープリンク URL を指定するオプションがあります。Experience Cloudの Mobile SDK およびサービスを使用しているアプリ開発者は、このフィールドに Mobile Services で設定されたフィンガープリンターの URL を入力する必要があります。 すべてが正しく設定されている場合、Facebook SDK は、アプリがインストールまたは起動されたときにこの URL をアプリケーションに渡します。

## SDK の設定 {#section_834CD3109175432B8173ECB6EA7DE315}

1. Facebook SDK を設定します。

   詳しくは、以下を参照してください。

   * [Getting Started with the Facebook SDK for iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [ディープリンクの設定](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. SDK を設定するには、`trackAdobeDeepLink` を呼び出して URL を SDK に渡します。

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >ディープリンク URL に `a.deeplink.id` という名前のキーがあることを確認してください。URL に `a.deeplink.id` パラメーターがない場合、コンテキストデータに URL パラメーターは追加されません。

アプリケーションが上記のように設定されている場合、現在の AMSDK バージョンは正常に機能し、ディープリンクデータがインストール／起動分析コールに正しく追加されます。

## サンプルアプリケーションでの機能の有効化 {#section_64C15E269E89424B8E3D029F88094620}

1. URL スキームを登録します。

   ディープリンク URL と同じ URL スキームを登録したことを確認します。

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Facebook SDK をリンクします。

   ![Facebook アセット](assets/link-fb-sdk.jpg)

1. `AppDelegate` を編集します。

   1. ヘッダーを読み込みます。

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. ディファードディープリンクにハンドルを追加します。

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. `trackAdobeDeepLink` API を呼び出してディープリンク URL を SDK に渡します。

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```
