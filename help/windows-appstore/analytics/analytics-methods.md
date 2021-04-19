---
description: Windows 8.1 Universal App Store SDKをAdobe Analyticsで使用するのに役立つ情報です。
seo-description: Windows 8.1 Universal App Store SDKをAdobe Analyticsで使用するのに役立つ情報です。
seo-title: Analytics メソッド
solution: Experience Cloud,Analytics
title: Analytics メソッド
topic-fix: Developer and implementation
uuid: 79db105c-216c-4061-97f3-a55954995e67
exl-id: 007bb801-55ef-4c5b-87fa-d0db42cde163
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 52%

---

# Analytics メソッド {#analytics-methods}

Windows 8.1 Universal App Store SDKをAdobe Analyticsで使用するのに役立つ情報です。

SDKは、現在、Analytics、ターゲット、Audience Managerを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Analyticsのメソッドの前には「Analytics」というプリフィックスが付きます。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

>[!TIP]
>
>winJS (JavaScript)から`winmd`メソッドを使用する場合、すべてのメソッドの最初の文字が自動的に小文字に変換されます。

* **TrackState(winJS:trackState)**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態は、「ホームダッシュボード」、「アプリ設定」、「カート」など、アプリで使用できる表示です。 これらの状態は Web サイト上のページによく似ており、`TrackState` コールにより、ページビュー数が増分されます。`state`が空の場合、レポートには「app name app version (build)」と表示されます。 レポートにこの値が表示される場合は、各`TrackState`呼び出しで`state`を設定していることを確認してください。

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

* **TrackAction(winJS:trackAction)**

   アプリのアクションを追跡します。アクションとは、「ログオン」、「バナーのタップ」、「フィード購読」など、測定対象のアプリで発生する操作です。

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

   ：Analytics 用に自動的に生成された訪問者識別子を返します。これは、初回起動時に生成され、その時点から保存および使用される、アプリ固有の一意の訪問者IDです。 このIDは、アプリのアップグレード後も保持され、アンインストール時に削除されます。

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

* **TrackLocation(winJS:trackLocation)**

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

* **TrackLifetime &#x200B; ValueIncrease(winJS:trackLifetime &#x200B; ValueIncrease)**

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

* **TrackTimed &#x200B; ActionStart(winJS:trackTimed &#x200B; ActionStart)**

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

* **TrackTimed &#x200B; ActionUpdate(winJS:trackTimed &#x200B; ActionUpdate)**

   `contextData` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。渡された`data`は、指定されたアクションの既存のデータに追加され、同じキーが既に`action`に定義されている場合は、データを上書きします。

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

* **TrackTimedActionExistsAsync(winJS:trackTimedActionExistsAsync)**

   渡された時間計測アクションが存在する場合はtrueを返し、存在しない場合はfalseを返します。

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

* **TrackTimed &#x200B; ActionEnd(winJS:trackTimed &#x200B; ActionEnd)**

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

   Analyticsトラッキングキューに保存されているすべてのヒットをクリアします。

   * このメッセージの構文を次に示します。

      ```csharp
      static void ClearTrackingQueue();
      ```

   * 次にコード例を示します。

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS:getQueueSizeAsync)**

   現在Analyticsキューに格納されているヒットの数を返します。

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
