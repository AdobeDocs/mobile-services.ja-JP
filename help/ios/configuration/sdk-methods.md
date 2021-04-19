---
description: iOS ライブラリが提供するメソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供するメソッドの一覧を以下に示します。
seo-title: 設定メソッド
solution: Experience Cloud,Analytics
title: 設定メソッド
topic-fix: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
exl-id: b6841808-8fa8-4090-8cb3-ce647a3d5d08
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 100%

---

# 設定メソッド {#configuration-methods}

iOS ライブラリが提供するメソッドの一覧を以下に示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。

* **setAppExtensionType**

   現在実行中の拡張機能の種類を特定するために、Adobe モバイル SDK の設定をおこないます。

   次のいずれかの値に設定します。
   * `ADBMobileAppExtensionTypeRegular`：エクステンションは本体アプリにバンドルされています。
   * `ADBMobileAppExtensionTypeStandAlone`：エクステンションは本体アプリにバンドルされていません。

   >[!TIP]
   >
   >このメソッドは、アプリにエクステンションがあるか、アプリがスタンドアロンエクステンションの場合に&#x200B;**のみ**&#x200B;使用してください。詳しくは、以下の *ADBMobileAppExtensionType* を参照してください。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Adobe Mobile ライブラリの現在のバージョンを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(NSString*) version;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown`：オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   現在のユーザーのプライバシーステータスを `status` に設定します。

   次のいずれかの値に設定します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown`：オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   現在のユーザーのライフタイム値を返します。デフォルト値は `0` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   自動的に生成された訪問者識別子を返します。これは、Adobe のサーバーによって生成される、アプリ固有の一意の訪問者 ID です。生成時に Adobe のサーバーに到達できない場合、Apple の CFUUID を使用して ID が生成されます。この値は、初回起動時に生成され、その時点から保存および使用されます。この ID は、アプリがアップグレードされても保持され、標準のアプリケーションバックアッププロセス中に保存および復元され、アンインストール時には削除されます。

   >[!TIP]
   >
   >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前のカスタムまたは自動生成された訪問者 ID が取得され、カスタムユーザー識別子として保存されます。詳しくは、以下の `userIdentifier` 行を参照してください。これによって、SDK をアップグレードしても訪問者データが保持されます。4.x SDK を新規インストールした場合、ユーザー識別子は `nil` なので、トラッキング識別子が使用されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   カスタムの識別子が設定されている場合は、ユーザーの識別子が返されます。カスタムの識別子が設定されていない場合は、`nil` が返されます。デフォルト値は `nil` です。

   >[!TIP]
   >
   >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前のカスタムまたは自動生成された訪問者 ID が取得され、カスタムユーザー識別子として保存されます。これにより、SDK をアップグレードしても訪問者データは保存されます。

   4.x SDK での新規インストールの場合、ユーザー識別子は設定されるまで `nil` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   現在のデバッグログの環境設定を返します。デフォルト値は `NO` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   デバッグログの環境設定を `debug` に設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   設定ファイル内のライフサイクルセッションのタイムアウト値にかかわらず、バックグラウンドから次に戻ったときに新しいセッションを開始しないように SDK に指示します。

   >[!TIP]
   >
   >このメソッドは、バックグラウンドにある間に通知を登録するアプリで使用されることを目的としており、アプリがバックグラウンドにある間に実行されるコードからのみ呼び出される必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、「[ライフサイクル指標](/help/ios/metrics.md)」を参照してください。

   >[!TIP]
   >
   >このメソッドを呼び出すのに望ましい場所は、`application:didFinishLaunchingWithOptions:` 内です。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   ライフサイクル指標収集時に追加データとして渡すことができます。

   このメソッドは、アプリのエントリポイントから呼び出す必要があります。該当する場合、`application:didFinishLaunchingWithOptions:` メソッドと `applicationWillEnterForeground:` メソッドのどちらかまたは両方を AppDelegate クラスに含めることができます。

   >[!IMPORTANT]
   >
   >`collectLifecycleDataWithAdditionalData:` を使用して SDK に渡されたデータは、SDK によって `NSUserDefaults` に保持されます。SDK は、`NSDictionary` 型または `NSString` 型ではない `NSNumber` パラメーターの値を削除します。`collectLifecycleDataWithAdditionalData:` を使用するには、SDK **バージョン 4.4** 以降が必要です。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   この API を使用して、ライフサイクルデータの収集を一時停止します。詳しくは、「[ライフサイクル指標](/help/ios/metrics.md)」を参照してください。

   >[!IMPORTANT]
   >
   >`applicationDidEnterBackground` delegate メソッドでは、まず `pauseCollectingLifecycleData` メソッドを呼び出す必要があります。
   >
   >この API は、セッション長指標が異常となった iOS 13 を搭載した、iPhone 7／7s 以前のデバイスでの問題を軽減するために提供されています。これは、iOS 13 で発生した不明な変更が原因です。iOS では、アプリケーションをバックグラウンドで実行する際、バックグラウンドタスクを完了するのに十分な時間が残りません。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。アプリケーションが閉じられるまで、この設定が使用されます。

   >[!IMPORTANT]
   >
   >`overrideConfigPath` を使用するには、SDK バージョン 4.2 以降が必要です。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   プッシュ通知用のデバイストークンを設定します。

   >[!IMPORTANT]
   >
   >このメソッドは、`application:didRegisterForRemoteNotificationsWithDeviceToken:`メソッド内でのみ使用する必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   IDFA を SDK に設定します。IDFA が SDK で設定されている場合、IDFA はライフサイクル内に送信されます。IDFA にはシグナル（ポストバック）でもアクセスできます。

   >[!TIP]
   >
   >広告サービスを使用している場合に&#x200B;**のみ**、Apple API から IDFA を取得してください。IDFA を取得し、正しく使用していない場合は、アプリが拒否されることがあります。
   >
   >アプリケーションで IDFA が必要な場合は、広告トラッキングに関するユーザーの環境設定の照会と IDFA 値の取得に関して [Apple のドキュメント](https://developer.apple.com/documentation/adsupport)を参照してください。
   >
   >iOS 14 以降では、IDFA 値を正しく取得するために、新しく [App Tracking Transparency フレームワーク](https://developer.apple.com/documentation/apptrackingtransparency)を実装する必要があります。
   * このメソッドの構文を次に示します。

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```
