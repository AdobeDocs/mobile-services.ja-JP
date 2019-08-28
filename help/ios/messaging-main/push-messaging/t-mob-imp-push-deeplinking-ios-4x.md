---
description: Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの adb_deeplink キーに含まれます。
seo-description: Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの adb_deeplink キーに含まれます。
seo-title: ディープリンクを使用したプッシュメッセージの実装
title: ディープリンクを使用したプッシュメッセージの実装
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの `adb_deeplink` キーに含まれます。

1. AppDelegate で、ディープリンク URL を返し、以下の場所で独自に処理できます。

   *  `application:didFinishLaunchingWithOptions`:

      プッシュクリックスルーが発生したときにアプリが動作していない場合は、`launchOptions` からプッシュペイロードを取得できます。ディープリンク URL は、`adb_deeplink` キーによってペイロード辞書に含まれます。

   * リモート通知用の delegate メソッド

      `didReceiveRemoteNotification:` アプリケーションまたは `didReceiveRemoteNotification:fetchCompletionHandler:` アプリケーションでは、キーを使用して `userInfo` 辞書にアクセスしてURLを取得 `adb_deeplink` できます。

   * The delegate methods for `UNUserNotificationCenter`

      `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` この方法では、キー内の `userInfo` 辞書からプッシュペイロードを取得 `adb_deeplink` できます。

以下に例を示します。

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

