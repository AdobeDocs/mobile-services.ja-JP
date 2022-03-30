---
description: Windows 8.1 ユニバーサルApp Storeライブラリが提供するクラスとメソッドです。
solution: Experience Cloud Services,Analytics
title: SDK メソッド
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 51%

---

# SDK メソッド {#sdk-methods}

Windows 8.1 ユニバーサルApp Storeライブラリが提供するクラスとメソッドです。

>[!TIP]
>
>消費時 `winmd` メソッドを winJS(JavaScript) から呼び出すと、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

* **GetVersion (winJS:getVersion)**

   Adobe Mobile ライブラリの現在のバージョンを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS:getPrivacyStatusAsync)**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` ：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      デフォルト値は [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) ファイル。

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

* **SetPrivacyStatus (winJS:setPrivacyStatus)**

   現在のユーザーのプライバシーステータスを `status` に設定します。次のいずれかの値に設定します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` ：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

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

* **GetLifetimeValue (winJS:getLifetimeValue)**

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

* **GetUserIdentifier (winJS:getUserIdentifier)**

   カスタム識別子が設定されている場合、カスタムユーザー識別子を返します。 カスタム識別子が設定されていない場合は null を返します。 デフォルト値は `null` です。

   >[!TIP]
   >
   >アプリをExperience Cloud3.x から 4.x SDK にアップグレードした場合、以前の ID（カスタム ID または自動生成 ID）が取得され、カスタムユーザー識別子として保存されます。 これにより、SDK をアップグレードしても訪問者データは保存されます。4.x SDK での新規インストールの場合、ユーザー識別子はです。 `null` 設定されるまで

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
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

      ```js
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

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging (winJS:setDebugLogging)**

   デバッグログの環境設定を `debugLogging` に設定します。デバッグログは、ライブラリのデバッグバージョンを使用している場合にのみ機能します。リリースバージョンでは、この設定は無視されます。

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

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、「[ライフサイクル指標](/help/windows-appstore/metrics.md)」を参照してください。

   >[!TIP]
   >
   >でこのメソッドを呼び出します。 `onResume()` メソッドを使用して、アプリケーション内の各アクティビティに追加できます。 また、グローバルなアプリケーションコンテキストではなく、アクティビティまたはサービスをコンテキストオブジェクトとして渡すことをお勧めします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void CollectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **LifecycleData の収&#x200B;集を一時停止します (winJS:pauseCollecting &#x200B; LifecycleData)**

   ライフサイクル指標が正しく計算されるように、アプリが一時停止されたことを SDK に通知します。例えば、一時停止時に、タイムスタンプを収集して、以前のセッションの長さを決定します。 また、これにより、アプリがクラッシュしなかったことをライフサイクルが正しく認識できるようにフラグが設定されます。 詳しくは、「[ライフサイクル指標](/help/windows-appstore/metrics.md)」を参照してください。

   >[!TIP]
   >
   >でこのメソッドを呼び出します。 `onPause()` メソッドを使用して、アプリケーション内の各アクティビティに追加できます。 また、グローバルなアプリケーションコンテキストではなく、アクティビティまたはサービスをコンテキストオブジェクトとして渡すことをお勧めします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
