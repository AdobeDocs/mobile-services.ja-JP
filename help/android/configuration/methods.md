---
description: 以下に、Android ライブラリによって提供されるメソッドのリストを示します。
keywords: android;library;mobile;sdk
seo-description: 以下に、Android ライブラリによって提供されるメソッドのリストを示します。
seo-title: 設定メソッド
solution: Experience Cloud,Analytics
title: 設定メソッド
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '985'
ht-degree: 100%

---


# 設定メソッド {#configuration-methods}

以下に、Android ライブラリによって提供されるメソッドのリストを示します。

## 初期設定 {#section_9169243ECC4744A899A8271F92090ECD}

次のメソッドは、メインアクティビティの `onCreate` メソッドで 1 回呼び出す必要があります。

* `setContext`このメソッドのコードサンプルを次に示します。

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## SDK 設定（設定クラス） {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * `AdobeDataCallback` インターフェイスを実装するオブジェクトを登録します。上書きされた「call」メソッドは、`Config.MobileDataEvent` 値と、トリガーイベントの `Map<String, Object>` 内の関連データを使用して呼び出されます。このコールバックをトリガーするイベントについて詳しくは、このトピックの下部にある「*MobileDataEventEnum*」を参照してください。

      >[!TIP]
      >
      >このメソッドには、バージョン 4.9.0 以降が必要です。

   * このメソッドの構文を次に示します。

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Adobe Mobile ライブラリの現在のバージョンを返します。
   * このメソッドの構文を次に示します。

      ```java
      public static String getVersion();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * 現在のユーザーのプライバシーステータスの enum 表現を返します。

      プライバシーステータスの値を次に示します。

      * `MOBILE_PRIVACY_STATUS_OPT_IN`：ヒットは即座に送信されます。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：ヒットは破棄されます。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

         レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。デフォルト値は `ADBMobileConfig.json` ファイルに設定します。
   * このメソッドの構文を次に示します。

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * 現在のユーザーのプライバシーステータスを `status` に設定します。

      プライバシーステータスは次のいずれかの値に設定できます。
      * `MOBILE_PRIVACY_STATUS_OPT_IN`：ヒットは即座に送信されます。これらのヒットは即座に送信されます。
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`：ヒットは破棄されます。これらのヒットは破棄されます。
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`：レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   * このメソッドの構文を次に示します。

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * 現在のユーザーのライフタイム値を返します。デフォルト値は `0` です。

   * このメソッドの構文を次に示します。

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * カスタム識別子が設定されている場合は、カスタムユーザー識別子が返されます。カスタム識別子が設定されていない場合は、`null` が返されます。デフォルト値は `null` です。

      >[!TIP]
      >
      >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前のカスタムまたは自動生成された訪問者 ID が取得され、カスタムユーザー識別子として保存されます。これによって、SDK をアップグレードしても訪問者データが保持されます。4.x SDK での新規インストールの場合は、ユーザー識別子は設定されるまでは `null` です。

   * このメソッドの構文を次に示します。

      ```java
      public static String&amp getUserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * ユーザー識別子を `identifier` に設定します。
   * このメソッドの構文を次に示します。

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * 現在のデバッグログの環境設定を返します。デフォルト値は `false` です。
   * このメソッドの構文を次に示します。

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * デバッグログの環境設定を `debugLogging` に設定します。
   * このメソッドの構文を次に示します。

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、「[ライフサイクル指標](/help/android/configuration/methods.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      追加のコンテキストデータを指定する場合：

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * （**バージョン 4.2 以降**）SDK のすべてのソリューションで使用するために、ライフサイクルデータが収集される必要があることを SDK に通知します。詳しくは、「[ライフサイクル指標](/help/android/metrics.md)」を参照してください。
   * このメソッドの構文を次に示します。

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
      ```

* **pauseCollecting&#x200B;LifecycleData**

   * ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、`onPause` は、タイムスタンプを収集して、以前のセッションの長さを決定します。また、これは、アプリがクラッシュしなかったことをライフサイクルが把握できるようにフラグを設定します。詳しくは、「[ライフサイクル指標](/help/android/metrics.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * （**バージョン 4.2 以降**）SDK で作成された通知に使用する小さいアイコンを設定します。このアイコンはステータスバーに表示され、ユーザーが通知センターで完全な通知を表示する際に表示されるセカンダリ画像です。
   * このメソッドの構文を次に示します。

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * （**バージョン 4.2 以降**）SDK で作成された通知に使用する大きいアイコンを設定します。このアイコンは、ユーザーが通知センターで完全な通知を表示する際に表示されるプライマリ画像です。
   * このメソッドの構文を次に示します。

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * （**バージョン 4.2以降**）アプリケーションの開始時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。アプリケーションが閉じられるまで、この設定が使用されます。
   * このメソッドの構文を次に示します。

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * プッシュ通知用のデバイストークンを設定します。
   * このメソッドの構文を次に示します。

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Google Play サービスから返された広告識別子の文字列を返す Callable を SDK に提供します。SDK は、バックグラウンドスレッドでこのタスクを実行し、Callable から返された値に基づく広告識別子の内部変数を設定します。

      >[!IMPORTANT]
      > 
      >獲得またはライフサイクルで広告識別子を使用する場合は、`Config.collectLifecycleData` を呼び出す前にこれを呼び出します。

      * このメソッドの構文を次に示します。

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * このメソッドのコードサンプルを次に示します。

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback インターフェイス {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
