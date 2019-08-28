---
description: Windows 8.1 ユニバーサルアプリストアライブラリによって提供されるクラスとメソッドです。
seo-description: Windows 8.1 ユニバーサルアプリストアライブラリによって提供されるクラスとメソッドです。
seo-title: SDKメソッド
solution: Marketing Cloud、Analytics
title: SDKメソッド
topic: 開発者と導入
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2epa
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Windows 8.1 ユニバーサルアプリストアライブラリによって提供されるクラスとメソッドです。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **getVersion（winJS:getVersion）**

   Adobe Mobile ライブラリの現在のバージョンを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **getPrivacyStatusAsync（winJS:getPrivacyStatusAsync）**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * `ADBMobilePrivacyStatusOptIn` - ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut` - ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **setPrivacyStatus（winJS:SetPrivacyStatus）**

   現在のユーザーのプライバシーステータスを `status` に設定します。次のいずれかの値に設定します。

   * `ADBMobilePrivacyStatusOptIn` - ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut` - ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **getLifetimeValue（winJS:getLifetimeValue）**

   現在のユーザーのライフタイム値を返します。デフォルトは 0 です。

   * このメソッドの構文を次に示します。

      ```csharp
      static float GetLifetimeValue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **getUserIdentifier（WinJS:getUserIdentifier）**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。カスタム識別子が設定されていない場合、null を返します。デフォルト値は `null` です。

   >[!TIP]
   >
   >アプリケーションがExperience Cloud3. x SDKから4. x SDKにアップグレードすると、以前のID（カスタムまたは自動生成）が取得され、カスタムユーザー識別子として保存されます。これにより、SDK をアップグレードしても訪問者データが保持されます。4.x SDK での新規インストールの場合、ユーザー識別子は設定されるまで `null` です。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **setUserIdentifier（WinJS:setUserIdentifier）**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **getDebugLogging（winJS:getDebugLogging）**

   現在のデバッグログの環境設定を返します。デフォルト値は `false` です。

   * このメソッドの構文を次に示します。

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **setDebugLogging（winJS:setDebugLogging）**

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

* **CollectLifecycleData（winJS:CollectLifecycleData）**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、[ライフサイクル指標](/help/windows-appstore/metrics.md)を参照してください。

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. また、グローバルの Application コンテキストではなく、Activity または Service をコンテキストオブジェクトとして渡すことをお勧めします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void CollectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollectingLifecycleData（WinJS:PauseCollectingLifecycleData）**

   ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、一時停止中にタイムスタンプを収集して、セッションの長さの計測を一時停止します。また、クラッシュ回数を正しく計測するためのフラグを設定します。詳しくは、[ライフサイクル指標](/help/windows-appstore/metrics.md)を参照してください。

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. また、グローバルの Application コンテキストではなく、Activity または Service をコンテキストオブジェクトとして渡すことをお勧めします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
