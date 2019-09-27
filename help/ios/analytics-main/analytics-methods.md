---
description: iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。
seo-title: Analyticsメソッド
solution: Marketing Cloud,Analytics
title: Analytics methods
topic: 開発者と導入
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

iOS ライブラリが提供する Adobe Analytics メソッドの一覧を以下に示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスを含む、複数のAdobe Experience cloudソリューションをサポートしています。 Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。`state` が空の場合は、レポートに「*app name app version (build)*」と表示されます。レポートにこの値が表示される場合は、各 `state` コールで `trackState` を設定しているかを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増やす唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   アプリのアクションを追跡します。Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, occur in your app.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

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
   >This method should only be called in code that runs while your app is in the background.

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

   ユーザーがいつビーコンの Proximit (圏内) に入ったかを追跡します。

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
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

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

   Requires SDK 4.1. Regardless of how many hits are currently queued, forces the library to send all hits in the offline queue.

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
   >キューを手動でクリアする場合は注意が必要です。 このプロセスを元に戻すことはできません。

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
   >このメソッドでは、ページビュー数は増分されません。

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
