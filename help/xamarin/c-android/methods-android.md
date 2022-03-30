---
description: Experience Cloudソリューション 4.x SDK 用 Xamarin コンポーネントの Android メソッド。
keywords: Xamarin
solution: Experience Cloud Services
title: Android メソッド
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Android メソッド{#android-methods}

Experience Cloudソリューション 4.x SDK 用 Xamarin コンポーネントの Android メソッド。

## 設定メソッド {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   現在のデバッグログの環境設定を返します。デフォルトは false です。

   * このメソッドの構文を次に示します。

      ```java
      public static Boolean DebugLogging;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   現在のユーザーのライフタイム値を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。
   * `ADBMobilePrivacyStatus.OptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatus.OptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatus.Unknown`：オフライン追跡が有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   デフォルト値は [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) ファイル。

   * このメソッドの構文を次に示します。

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   カスタム識別子が設定されている場合は、この識別子を返します。 カスタム識別子が設定されていない場合は、null を返します。 デフォルト値は `null` です。

   * このメソッドの構文を次に示します。

      ```java
      public static UserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **バージョン**

   ライブラリのバージョンを取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static string Version;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、一時停止時に、タイムスタンプを収集して、以前のセッションの長さを決定します。 また、これにより、アプリがクラッシュしなかったことをライフサイクルが正しく認識できるようにフラグが設定されます。 詳しくは、「[ライフサイクル指標](/help/android/metrics.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity activity)**

   （4.2 以降）SDK のすべてのソリューションで使用するために、ライフサイクルデータを収集する必要があることを SDK に通知します。 詳しくは、「[ライフサイクル指標](/help/android/metrics.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity activity)**

   （4.2 以降）SDK のすべてのソリューションで使用するために、ライフサイクルデータを収集する必要があることを SDK に通知します。 詳しくは、「[ライフサイクル指標](/help/android/metrics.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   （4.2 以降） `ADBMobile JSON` 設定ファイルに保存されます。 アプリケーションが閉じられるまで、この設定が使用されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   （4.2 以降）SDK で作成される通知に使用する大きいアイコンを設定します。 このアイコンは、ユーザーが通知センターで完全な通知を表示する際に表示されるプライマリ画像です。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   （4.2 以降）SDK で作成される通知に使用する小さいアイコンを設定します。 このアイコンはステータスバーに表示され、ユーザーが通知センターで完全な通知を表示する際に表示されるセカンダリ画像です。

   * このメソッドの構文を次に示します。

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics メソッド {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Analytics 用に自動的に生成された ID を返します。 これは、初回起動時に生成され、その時点から保存されて使用される、アプリ固有の一意の ID です。 この ID は、アプリがアップグレードされても保持され、アンインストール時に削除されます。

   * このメソッドの構文を次に示します。

      ```java
      public static string TrackingIdentifier;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。`States` は、「タイトル画面」、「レベル 1」、「一時停止」など、アプリで使用可能なビューです。 これらの状態は Web サイト上のページによく似ており、`TrackState` コールにより、ページビュー数が増分されます。state が空の場合、レポートに「app name app version (build)」と表示されます。 レポートにこの値が表示される場合は、各 `TrackState` 呼び出し。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   アプリのアクションを追跡します。アクションとは、アプリ内で測定に価する重要な操作のことで、「deaths」、「level gained」、「feed subscriptions」などの指標があります。

   >[!TIP]
   >
   >
   >アプリがバックグラウンドになっているときに、コードが実行される（バックグラウンドデータの取得など）可能性がある場合は、代わりに `trackActionFromBackground` を使用します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   現在地点の緯度と経度の座標を送信します。また、 `ADBMobileConfig.json` ファイルを使用して、パラメーターとして指定された場所がいずれかの POI 内にあるかどうかを判断します。 現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`TrackLocation` コールで送信されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   ユーザーがいつビーコンの Proximity (圏内) に入ったかを追跡します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   ユーザーがビーコンの Proximity を離れた場合に、ビーコンデータをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   ユーザーのライフタイム値に値を加算します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   指定アクションの時間計測を開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   > この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   データを渡して、指定されたアクションに関連付けられているコンテキストデータを更新します。渡されたデータは、指定されたアクションの既存のデータに追加され、同じキーが既にアクションに定義されている場合は、データを上書きします。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   時間計測アクションを終了します。

   * このメソッドの構文を次に示します。

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   時間計測アクションが進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   現在キューに格納されているヒット数に関係なく、オフラインキュー内のすべてのヒットを強制的に送信します。

   * このメソッドの構文を次に示します。

      ```java
      public static void SendQueuedHits();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   オフラインキューからすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void ClearQueue(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   現在オフラインキュー内にあるヒットの数を取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static long QueueSize(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience CloudID メソッド {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Experience Cloud ID を ID サービスから取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static string MarketingCloudId;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Experience CloudID を使用して、各訪問者に関連付ける追加の顧客 ID を設定できます。 訪問者 API は、同じ訪問者に対して複数の顧客 ID と、異なる顧客 ID の範囲を区別するための顧客タイプ識別子を受け取ります。このメソッドは、JavaScript ライブラリの `setCustomerIDs` に相当します。

   * このメソッドの構文を次に示します。

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target メソッド {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   設定した Target サーバーにリクエストを送信し、 `Action<NSDictionary>` コールバック。

   * このメソッドの構文を次に示します。

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   次を作成する便利なコンストラクター： `ADBTargetLocationRequest` オブジェクトに指定したパラメーターを含めます。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   `ADBTargetLocationRequest` を作成します。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   アプリから Target の Cookie をクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void ClearCookies(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   取得された最も直近の訪問者プロファイルを返します。まだシグナルが送信されていない場合は、nil を返します。 訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`NSUserDefaults` に保存されます。

   * このメソッドの構文を次に示します。

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   現在の `DPID`.

   * このメソッドの構文を次に示します。

      ```java
      public static string Dpuuid; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   現在の `DPUUID`.

   * このメソッドの構文を次に示します。

      ```java
      public static string AudienceDpuuid; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   を設定します。 `dpid` および `dpuuid`. If `dpid` および `dpuuid` が設定されている場合は、各シグナルと共に送信されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   特性を持つシグナルを Audience Management に送信し、 `Action<NSDictionary>` コールバック。

   * このメソッドの構文を次に示します。

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **リセット**

   Audience Manager をリセット `UUID` 現在の訪問者プロファイルを削除します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Reset ();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       AudienceManager.Reset ();
      ```

## ビデオ {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

ビデオ分析について詳しくは、 [ビデオ分析](/help/android/analytics-main/video-qs.md).

* **MediaSettings**

   指定したパラメーターと共に `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   広告ビデオの追跡に使用する `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **オープン**

   追跡する `ADBMediaSettings` オブジェクトを開きます。

   * このメソッドの構文を次に示します。

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **閉じる**

   name という名前のメディアアイテムを閉じます。

   * このメソッドの構文を次に示します。

      ```java
      public static void Close(string name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Close (settings.Name); 
      ```

* **Play**

   指定された名前のメディアアイテムを指定されたオフセット（秒）で再生したことを記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Play ( string name, double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Complete**

   指定されたオフセットでメディアアイテムが再生完了されたことを手動で記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Complete (string name, double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **停止**

   指定された offset でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Click**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Click ( string name, double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **追跡**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.Track (settings.Name, null); 
      ```
