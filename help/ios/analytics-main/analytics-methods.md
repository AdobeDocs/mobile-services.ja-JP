---
description: iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。
seo-title: Analytics メソッド
solution: Experience Cloud,Analytics
title: Analytics メソッド
topic-fix: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
exl-id: 327ec44a-be15-47af-a2c8-a373124999ad
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---

# Analytics メソッド {#analytics-methods}

iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。メソッドには、ソリューションに応じたプレフィックスが付きます。Experience Cloud ID メソッドの場合、プレフィックスは「`track`」です。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

* **trackState:&#x200B;data:**

   状態とは、アプリで使用可能なビューのことで、`home dashboard`、`app settings`、`cart` などがあります。これらの状態は Web サイト上のページによく似ており、`trackState` コールにより、ページビュー数が増分されます。`state` が空の場合は、レポートに「*app name app version (build)*」と表示されます。レポートにこの値が表示される場合は、各 `state` コールで `trackState` を設定しているかを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   アプリのアクションを追跡します。`feed subscriptions`、`logons`、`banner taps` などの指標など、測定するアクションはアプリで発生します。

   >[!TIP]
   >
   >アプリがバックグラウンドになっているときに、コードが実行される（バックグラウンドデータの取得など）可能性がある場合は、代わりに `trackActionFromBackground` を使用します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Analytics トラッキング識別子を取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   バックグラウンドで発生したアクションを追跡し、特定のシナリオでライフサイクルイベントが実行されないようにします。

   >[!TIP]
   >
   >このメソッドは、アプリがバックグラウンドになっているときに実行されるコードでのみ呼び出す必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   現在の XY 座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` コールで送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   ユーザーがいつビーコンの Proximity (圏内) に入ったかを追跡します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   ユーザーがビーコンの Proximity を離れた場合に、ビーコンデータをクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   `action` という名前の時間計測アクションを開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   `data` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。渡された `data` は、アクションの既存のデータに追加されます。`action` に対して同じキーが既に定義されている場合は、データが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   時間計測アクションを終了します。`block` を指定した場合は、最終時刻値にアクセスして、最終ヒットを送信する前に、`data` を操作することができます。

   >[!TIP]
   >
   >`block` を指定する場合、ヒットを送信するには `YES` を返す必要があります。`nil` に `block` を指定すると、最終ヒットが送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   時間計測アクションが進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   SDK 4.1 が必要です。現在キューに格納されているヒットの数にかかわらず、オフラインキュー内のすべてのヒットを強制的に送信します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   現在オフラインキュー内に格納されているヒットの数を取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   オフラインキューからすべてのヒットをクリアします。

   >[!CAUTION]
   >
   >キューを手動でクリアするときは注意が必要です。このプロセスを元に戻すことはできません。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   プッシュメッセージのクリックスルーを追跡します。

   >[!IMPORTANT]
   >
   >このメソッドは、ページビュー数を増分しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
