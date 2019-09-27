---
description: Windows 8.1 ユニバーサルアプリストア SDK を Adobe Analytics で使用する際に役立つ情報です。
seo-description: Windows 8.1 ユニバーサルアプリストア SDK を Adobe Analytics で使用する際に役立つ情報です。
seo-title: Analyticsメソッド
solution: Marketing Cloud,Analytics
title: Analyticsメソッド
topic: 開発者と導入
uuid: 79db105c-216c-4061-97f3-a55954995e67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Windows 8.1 ユニバーサルアプリストア SDK を Adobe Analytics で使用する際に役立つ情報です。

SDKは、現在、Analytics]、Target]、Audience Managerを含む、複数のAdobe Experience cloudソリューション]をサポートしています。 これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。Analytics メソッドには「Analytics」というプレフィックスが付けられています。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **TrackState(winJS:trackState)**

   オプションのコンテキストデータでアプリ状態を追跡します。状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。これらの状態は Web サイト上のページによく似ており、`TrackState` コールはページビュー数を増分します。`state` が空の場合は、レポートに「app name app version (build)」と表示されます。レポートにこの値がある場合、各 `state` 呼び出しで `TrackState` を設定していることを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増やす唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS:trackAction)**

   アプリのアクションを追跡します。アクションとは、アプリ内で測定対象となる重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **GetTrackingIdentifierAsync (winJS:getTrackingIdentifierAsync)**

   Analytics 用に自動的に生成された訪問者識別子を返します。これは、初回起動時に生成され、それ以降、保存および使用されるアプリ固有の一意の訪問者 ID です。この ID は、アプリがアップグレードされても保持されますが、アンインストール時には削除されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **TrackLocation (winJS:trackLocation)**

   現在の XY 座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **TrackLifetime &#x200B; valueIncrease (winJS:trackLifetime &#x200B; valueIncrease)**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **TrackTimed &#x200B; ActionStart(winJS:trackTimed &#x200B; actionStart)**

   `action` という名前の時間計測アクションを開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS:trackTimed &#x200B; actionUpdate)**

   `contextData` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   指定された時間計測アクションが存在する場合は true を返し、存在しない場合は false を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **TrackTimed&#x200B;ActionEnd (winJS: trackTimed&#x200B;ActionEnd)**

   時間計測アクションを終了します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Analytics 追跡キューに格納されているすべてのヒットをクリアします。

   * このメッセージの構文を次に示します。

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 次にコードの例を示します。

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   現在 Analytics キューに格納されているヒットの数を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
