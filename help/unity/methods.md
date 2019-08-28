---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile. csメソッド
solution: Marketing Cloud，開発者
title: ADBMobile. csメソッド
uuid: af504934- febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## 設定メソッド

* **CollectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、[ライフサイクル指標](/help/ios/metrics.md)を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void CollectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.CollectLifecycleData(); 
      ```

* **EnableLocalNotifications（iOS のみ）**

   アプリのローカル通知を有効にします。

   * このメソッドの構文を次に示します。

      ```java
      public static void EnableLocalNotifications();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.EnableLocalNotifications(); 
      ```

* **GetDebugLogging**

   現在のデバッグログの環境設定を返します。デフォルト値は `false` です。

   * このメソッドの構文を次に示します。

      ```java
      public static bool GetDebugLogging();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   現在のユーザーのライフタイム値を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static double GetLifetimeValue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。
   * `MOBILE_PRIVACY_STATUS_OPT_IN`:ヒットはすぐに送信されます。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`:ヒットは破棄されます。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`：オフライン追跡が有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。デフォルト値は [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) ファイルに設定します。

   * このメソッドの構文を次に示します。

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。カスタム識別子が設定されていない場合、null を返します。デフォルト値は `null` です。

   * このメソッドの構文を次に示します。

      ```java
      public static string GetUserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var userId = ADBMobile.GetUserIdentifier(); 
      ```

* **GetVersion**

   ライブラリのバージョンを取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static string GetVersion();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive（iOS のみ）**

   設定ファイル内のライフサイクルセッションのタイムアウト値にかかわらず、バックグラウンドから次に戻ったときに新しいセッションを開始しないように SDK に指示します。

   >[!TIP]
   >
   >このメソッドは、バックグラウンドで通知を登録するアプリで使用することを目的としており、アプリがバックグラウンドにある間に実行されるコードからのみ呼び出される必要があります。

   * このメソッドの構文を次に示します。

      ```java
      public static void KeepLifecycleSessionAlive(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.KeepLifecycleSessionAlive(); 
      ```

* **PauseCollectingLifecycleData（Android のみ）**

   ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、一時停止中にタイムスタンプを収集して、セッションの長さの計測を一時停止します。また、クラッシュ回数を正しく計測するためのフラグを設定します。詳しくは、[ライフサイクル指標](/help/android/metrics.md)を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.PauseCollectingLifecycleData(); 
      ```

* **SetContext（Android のみ）**

   unityPlayerの現在のアクティビティからアプリケーションコンテキストを設定する必要があることをSDKに示します。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetContext();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.SetContext(); 
      ```

* **SetDebugLogging**

   デバッグログの環境設定を有効に設定します。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetDebugLogging (bool enabled); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.SetDebugLogging(true); 
      ```

* **SetPrivacyStatus**

   現在のユーザーのプライバシーステータスをステータスに設定します。次のいずれかに設定します。

   * `MOBILE_PRIVACY_STATUS_OPT_IN`:ヒットはすぐに送信されます。
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`:ヒットは破棄されます。
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`：オフライン追跡が有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus); 
      ```

   * 以下に、この構文のコードサンプルを示します。

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   ユーザー識別子を userId に設定します。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetUserIdentifier(string userId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId"); 
      ```

## Analyticsのメソッド

* **GetTrackingIdentifier**

   Analytics トラッキング識別子を取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static string GetTrackingIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier(); 
      ```

* **TrackState**

   オプションのコンテキストデータでアプリ状態を追跡します。状態は、「title screen」、「level 1」、「pause」など、アプリで利用できる表示です。これらの状態は Web サイト上のページによく似ており、`TrackState` コールはページビュー数を増分します。

   If state is empty, it displays as *`app name app version (build)`* in reports. レポートにこの値がある場合、各 `TrackState` 呼び出しで state を設定していることを確認してください。

   >[!TIP]
   >
   >これはページビュー数が増える唯一のトラッキング呼び出しです。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var contextData = new Dictionary<string, object>); 
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   アプリのアクションを追跡します。アクションとは、アプリ内で計測に価する重要な操作のことで、「deaths」、「level gained」、「feed subscriptions」などの指標があります。

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground（iOS のみ）**

   バックグラウンドで発生したアクションを追跡します。これにより、特定の状況でライフサイクルイベントが発生するのを抑えます。

   >[!TIP]
   >
   >このメソッドは、アプリケーションがバックグラウンドにある間に実行されるコードでのみ呼び出す必要があります。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   現在地点の緯度と経度の座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、TrackLocation 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null); 
      ```

* **TrackBeacon**

   ユーザーがいつビーコンの Proximit (圏内) に入ったかを追跡します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata); 
      ```

* **TrackingClearCurrentBeacon**

   ユーザーがビーコンの Proximity を離れた場合に、ビーコンデータをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackingClearCurrentBeacon(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   ユーザーのライフタイム値に値を加算します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   指定アクションの時間計測を開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   特定のアクションに関連付けられたコンテキストデータを指定データで更新します。渡されたデータは、特定のアクションの既存のデータに追加され、同じキーが既にアクションに定義されている場合は、データを上書きします。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var contextData = new Dictionary<string, object>; 
      contextData.Add("checkpoint", "1:32"); 
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   時間計測アクションを終了します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionEnd(string action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackTimedActionEnd("level2"); 
      ```

* **TrackingTimedActionExists**

   時間計測が進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2"); 
      ```

* **TrackingSendQueuedHits**

   現在キューに格納されている件数にかかわらず、オフラインキューのすべてのヒットを強制的に送信します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   オフラインキューからすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackingClearQueue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADBMobile.TrackingClearQueue(); 
      ```

* **TrackingGetQueueSize**

   現在オフラインキュー内に格納されているヒットの数を取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static int TrackingGetQueueSize();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience Cloud IDメソッド

* **GetMarketingCloudID**

   Experience Cloud ID を ID サービスから取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static string GetMarketingCloudID(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Experience Cloud ID を使用すると、追加の顧客 ID を設定して、各訪問者に関連付けることができます。独自の識別子を使えば、同じ訪問者に対して複数の顧客 ID をセットすることも可能です。このメソッドは、JavaScript ライブラリの setCustomerIDs に相当します。

   * このメソッドの構文を次に示します。

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var ids = new Dictionary<string, object> (); 
      ids.Add ("player1", "jimbob"); 
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

