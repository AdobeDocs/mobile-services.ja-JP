---
description: Adobe Analyticsで Windows 8.1 Universal App Store SDK を使用する際に役立つ情報です。
solution: Experience Cloud Services,Analytics
title: Analytics メソッド
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 53%

---

# Analytics メソッド {#analytics-methods}

Adobe Analyticsで Windows 8.1 Universal App Store SDK を使用する際に役立つ情報です。

SDK は現在、Analytics、Target、Audience Managerなど、複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Analytics メソッドの場合、プレフィックスは「Analytics」です。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

>[!TIP]
>
>消費時 `winmd` メソッドを winJS(JavaScript) から呼び出すと、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

* **TrackState (winJS:trackState)**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。 これらの状態は Web サイト上のページによく似ており、`TrackState` コールにより、ページビュー数が増分されます。If `state` が空の場合は、レポートに「app name app version (build)」と表示されます。 レポートにこの値が表示される場合は、次の設定を行っていることを確認してください： `state` 各 `TrackState` 呼び出し。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

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

   アプリのアクションを追跡します。アクションとは、アプリ内で測定に価する重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

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

   ：Analytics 用に自動的に生成された訪問者識別子を返します。これは、初回起動時に生成され、その時点から保存されて使用される、アプリ固有の一意の訪問者 ID です。 この ID は、アプリがアップグレードされても保持され、アンインストール時に削除されます。

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

* **TrackLifetime &#x200B; ValueIncrease (winJS:trackLifetime &#x200B; ValueIncrease)**

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

* **TrackTimed ActionStart (&#x200B;winJS:trackTimed ActionStart&#x200B;)**

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

* **TrackTimed ActionUpdate &#x200B; (winJS:trackTimed ActionUpdate&#x200B;)**

   `contextData` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。この `data` 渡された値は、特定のアクションの既存のデータに追加され、同じキーが既に `action`.

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

* **TrackTimedActionExistsAsync (winJS:trackTimedActionExistsAsync)**

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

* **TrackTimed ActionEnd (&#x200B;winJS:trackTimed ActionEnd&#x200B;)**

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

* **ClearTrackingQueue (winJS:clearTrackingQueue)**

   Analytics トラッキングキューから保存されているすべてのヒットをクリアします。

   * このメッセージの構文を次に示します。

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 次にコードサンプルを示します。

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS:getQueueSizeAsync)**

   Analytics キューに現在保存されているヒット数を返します。

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
