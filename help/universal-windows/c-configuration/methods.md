---
description: Universal Windows Platform ライブラリで提供されているクラスとメソッドです。
seo-description: Universal Windows Platform ライブラリで提供されているクラスとメソッドです。
seo-title: SDKメソッド
solution: Marketing Cloud,Analytics
title: SDK methods
topic: 開発者と導入
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Universal Windows Platform ライブラリで提供されているクラスとメソッドです。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion (winJS:getVersion)**

   Adobe Mobile ライブラリの現在のバージョンを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS:getPrivacyStatusAsync)**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * `ADBMobilePrivacyStatusOptIn` - Hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut`  — ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown`  — レポートスイートでタイムスタンプが有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      The default value is set in the `ADBMobileConfig.json` config file. 詳しくは、ADBMobileConfig.json設定フ [ァイルを参照してください](/help/universal-windows/c-configuration/c.json.md)。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Here are the code samples for this method:

      **Cシャープ**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS:setPrivacyStatus)**

   現在のユーザーのプライバシーステータスを `status` に設定します。次のいずれかの値に設定します。
   * `ADBMobilePrivacyStatusOptIn` - hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - hits are discarded.
   * `DBMobilePrivacyStatusUnknown`  — レポートスイートでタイムスタンプが有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      * このメソッドの構文を次に示します。

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * このメソッドのコード例を次に示します。

         **Cシャープ**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS:getLifetimeValue)**

   現在のユーザーのライフタイム値を返します。デフォルト値は `0` です。

   * このメソッドの構文を次に示します。

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **GetUserIdentifier (winJS:getUserIdentifier)**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。Returns `null` if a custom identifier is not set.
デフォルト値は `null` です。

   >[!IMPORTANT]
   >
   >アプリがExperience Cloud 3.xから4.x SDKにアップグレードされた場合、以前のIDサービス（カスタムまたは自動生成）が取得され、カスタムユーザーIDとして保存されます。 これにより、SDK をアップグレードしても訪問者データが保持されます。4.x SDK での新規インストールの場合、ユーザー識別子は設定されるまで `null` です。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS:setUserIdentifier)**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging (winJS:getDebugLogging)**

   現在のデバッグログの環境設定を返します。デフォルト値は `false` です。

   * このメソッドの構文を次に示します。

      ```csharp
      static bool GetDebugLogging();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS:setDebugLogging)**

   デバッグログの環境設定を `debugLogging` に設定します。デバッグログはデバッグバージョンのライブラリを使用している場合にのみ機能し、リリースバージョンを使用している場合、この設定は無視されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS:collectLifecycleData)**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。For more information, see  [Lifecycle metrics](/help/universal-windows/metrics.md).

   * このメソッドの構文を次に示します。

      ```csharp
      static void CollectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS:pauseCollecting &#x200B; LifecycleData)**

   ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、一時停止中にタイムスタンプを収集して、セッションの長さの計測を一時停止します。また、クラッシュ回数を正しく計測するためのフラグを設定します。詳しくは、[ライフサイクル指標](/help/universal-windows/metrics.md)を参照してください。

   * このメソッドの構文を次に示します。

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
