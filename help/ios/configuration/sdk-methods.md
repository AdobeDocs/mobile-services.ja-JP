---
description: iOS ライブラリが提供するメソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供するメソッドの一覧を以下に示します。
seo-title: 設定方法
solution: Marketing Cloud,Analytics
title: 設定方法
topic: 開発者と導入
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

iOS ライブラリが提供するメソッドの一覧を以下に示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスを含む、複数のAdobe Experience cloudソリューションをサポートしています。

* **setAppExtensionType**

   現在実行中のエクステンションの種類を判断するように Adobe Mobile SDK 設定を指定します。

   次のいずれかの値に設定します。
   * `ADBMobileAppExtensionTypeRegular`  — 拡張は、含まれるアプリにバンドルされています。
   * `ADBMobileAppExtensionTypeStandAlone`  — 拡張は、含まれるアプリにバンドルされていません。
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

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

   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut`  — ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` - オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

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

   * `ADBMobilePrivacyStatusOptIn`  — ヒットは直ちに送信されます。
   * `ADBMobilePrivacyStatusOptOut`  — ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` - オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

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

   自動的に生成された訪問者識別子を返します。これは、アドビのサーバーによって生成される、アプリ固有の一意の訪問者 ID です。生成時にアドビのサーバーに到達できない場合、ID は Apple の CFUUID を使用して生成されます。値は初期起動時に生成され、保存されて、その時点から使用されます。この ID はアプリをアップグレードしても保持され、標準的なアプリケーションバックアッププロセス時に保存および復元され、アンインストール時に削除されます。

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to the 4.x SDK, the previous custom or automatically generated visitor ID is retrieved and stored as the custom user identifier. 詳しくは、以下の `userIdentifier` 行を参照してください。これによって、SDK をアップグレードしても訪問者データが保持されます。4.x SDK を新規インストールした場合、ユーザー識別子は `nil` なので、トラッキング識別子が使用されます。

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
   >アプリがExperience Cloud 3.xから4.x SDKにアップグレードされた場合、以前にカスタムまたは自動生成された訪問者IDが取得され、カスタムユーザーIDとして保存されます。 これにより、SDK をアップグレードしても訪問者データは保存されます。

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
   >このメソッドは、バックグラウンドで通知を登録するアプリに対して使用されることを目的としており、アプリがバックグラウンドで実行されている間に実行されるコードからのみ呼び出す必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、[ライフサイクル指標](/help/ios/metrics.md)を参照してください。

   >[!TIP]
   >
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

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

   This method must be called from the entry point of your app. Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. SDK は、`NSDictionary` 型または `NSString` 型ではない `NSNumber` パラメーターの値を削除します。To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。アプリケーションが閉じられるまで、この設定が使用されます。

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

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
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

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

   IDFA を SDK に設定します。SDK で IDFA が設定されている場合、ライフサイクルで IDFA が送信されます。IDFA にはシグナル（ポストバック）でもアクセスできます。

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. IDFA を取得し、正しく使用していない場合は、アプリが拒否されることがあります。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
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

