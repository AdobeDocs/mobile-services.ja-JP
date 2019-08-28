---
description: Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネントの iOS メソッド。
keywords: Xamarin
seo-description: Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネントの iOS メソッド。
seo-title: iOSのメソッド
solution: Marketing Cloud，開発者
title: iOSのメソッド
uuid: d6a056db-80c1-44d0-970f- c961ad01b0bc
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# iOS methods{#ios-methods}

Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネントの iOS メソッド。

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、[ライフサイクル指標](/help/ios/metrics.md)を参照してください。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **debugLogging**

   現在のデバッグログの環境設定を返します。デフォルト値は `false` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   デバッグログの環境設定を有効に設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void SetDebugLogging(bool enabled); 
      
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      
* **LifetimeValue**

   現在のユーザーのライフタイム値を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static double LifetimeValue(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue(); 
      ```

* **PrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。
   * `ADBMobilePrivacyStatus.OptIn` - ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatus.OptOut` - ヒットは破棄されます。
   * ADBMobilePrivacyStatus.Unknown - オフライン追跡が有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が無効になっている場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * このメソッドの構文を次に示します。

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       var privacyStatus = ADBMobile.PrivacyStatus(); 
      ```


* **SetPrivacyStatus**

   現在のユーザーのプライバシーステータスをステータスに設定します。次のいずれかに設定します。
   * `ADBMobilePrivacyStatus.OptIn` - ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatus.OptOut` - ヒットは破棄されます。
   * `ADBMobilePrivacyStatus.Unknown` - オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。カスタム識別子が設定されていない場合、null を返します。デフォルト値は `null` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。カスタム識別子が設定されていない場合、null を返します。デフォルト値は `null` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string UserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   ライブラリのバージョンを取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string Version();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive（iOS のみ）**

   設定ファイル内のライフサイクルセッションのタイムアウト値にかかわらず、バックグラウンドから次に戻ったときに新しいセッションを開始しないように SDK に指示します。

   >[!TIP]
   >
   >このメソッドは、バックグラウンドで通知を登録するアプリで使用することを目的としており、アプリがバックグラウンドにある間に実行されるコードからのみ呼び出される必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
       public static void KeepLifecycleSessionAlive();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Analytics トラッキング識別子を取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   オプションのコンテキストデータでアプリ状態を追跡します。状態は、「title screen」、「level 1」、「pause」など、アプリで利用できる表示です。これらの状態は、Webサイト上のページと同様に `TrackState` 、呼び出しページビュー数を増分します。状態が空の場合、レポートには「アプリ名アプリのバージョン（ビルド）」と表示されます。レポートにこの値がある場合、各 `TrackState` 呼び出しで state を設定していることを確認してください。

   [!TIP]
   >これはページビュー数が増える唯一のトラッキング呼び出しです。
   >
   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   アプリのアクションを追跡します。アクションとは、アプリ内で計測に価する重要な操作のことで、「deaths」、「level gained」、「feed subscriptions」などの指標があります。

   >[!TIP]
   If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground（iOS のみ）**

   バックグラウンドで発生したアクションを追跡します。これにより、特定の状況でライフサイクルイベントが発生するのを抑えます。

   >[!TIP]
   このメソッドは、アプリケーションがバックグラウンドにある間に実行されるコードでのみ呼び出す必要があります。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   現在地点の緯度と経度の座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`TrackLocation` 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   ユーザーがいつビーコンの Proximit (圏内) に入ったかを追跡します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   ユーザーがビーコンの Proximity を離れた場合に、ビーコンデータをクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   ユーザーのライフタイム値に値を加算します。

   * このメソッドの構文を次に示します。

      public nbsp;static void trackLifetimeValueValueIncrement（double amount， NSDictionary cdata）;

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   指定アクションの時間計測を開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   特定のアクションに関連付けられたコンテキストデータを指定データで更新します。渡されたデータは、特定のアクションの既存のデータに追加され、同じキーが既にアクションに定義されている場合は、データを上書きします。

   >[!TIP]
   この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   時間計測アクションを終了します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      }); 
      
* **TrackingTimedActionExists**

   時間指定アクションが進行中であるかどうかを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   現在キューに格納されている件数にかかわらず、オフラインキューのすべてのヒットを強制的に送信します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   オフラインキューからすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   現在オフラインキュー内に格納されているヒットの数を取得します。

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Experience Cloud ID を ID サービスから取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Experience Cloud ID を使用すると、追加の顧客 ID を設定して、各訪問者に関連付けることができます。独自の識別子を使えば、同じ訪問者に対して複数の顧客 ID をセットすることも可能です。このメソッドは、JavaScript ライブラリの setCustomerIDs に相当します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
       ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target メソッド {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
       ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
       ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
       Console.WriteLine  (context); 
       });
      ```

* **TargetCreateRequest**

   指定したパラメーターを持つ `ADBTargetLocationRequest` オブジェクトを作成する便利なコンストラクターです。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   を作成 `ADBTargetLocationRequest`します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   アプリから対象の cookie をクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   取得された最も直近の訪問者プロファイルを返します。まだシグナルが送信されていない場合は nil を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`NSUserDefaults` に保存されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   現在の DPID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string AudienceDpid ();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   現在の DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   dpid および dpuuid を設定します。dpid および dpuuid が設定されている場合、各シグナルと共に送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Audience Manager UUID をリセットし、現在の訪問者プロファイルを削除します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void AudienceReset ();
      ```

   * このメソッドの構文を次に示します。

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

詳しくは、[ビデオの分析](/help/ios/getting-started/dev-qs.md)を参照してください。

* **MediaCreateSettings**

   指定したパラメーターと共に `ADBMediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   広告ビデオの追跡に使用する `ADBMediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   追跡する `ADBMediaSettings` オブジェクトを開きます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   指定された名前のメディアアイテムを閉じます。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   指定された名前のメディアアイテムを指定されたオフセット（秒）で再生したことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   指定されたオフセットでメディアアイテムが再生完了された、と手動で記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   指定されたオフセットでビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
