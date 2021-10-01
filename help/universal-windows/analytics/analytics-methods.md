---
description: Adobe Analyticsで Universal Windows Platform SDK を使用する際に役立つ情報です。
solution: Experience Cloud,Analytics
title: Analytics メソッド
topic-fix: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
exl-id: 3ceaedfa-274f-4dc7-9e4c-15233d09f935
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 58%

---

# Analytics メソッド {#analytics-methods}

Adobe Analyticsで Universal Windows Platform SDK を使用する際に役立つ情報です。

SDK は現在、Analytics、Target、Audience Managerを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Analytics メソッドの場合、プレフィックスは「Analytics」です。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

>[!TIP]
>
>winJS(JavaScript) の `winmd` メソッドを使用すると、すべてのメソッドの最初の文字が自動的に小文字に変換されます。

* **TrackState(winJS:trackState)**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、「home dashboard」、「app settings」、「cart」など、アプリで使用可能なビューです。 これらの状態は Web サイト上のページによく似ており、`TrackState` コールにより、ページビュー数が増分されます。`state` が空の場合は、レポートに「app name app version (build)」と表示されます。 レポートにこの値が表示される場合は、各 `TrackState` 呼び出しで `state` を設定していることを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS:trackAction)**

   アプリのアクションを追跡します。アクションとは、アプリ内で測定に価する重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS:getTrackingIdentifierAsync)**

   Analytics 用に自動的に生成された訪問者 ID を返します。 これは、初回起動時に生成され、その時点から保存および使用される、アプリ固有の一意の訪問者 ID です。 この ID は、アプリをアップグレードしても保持され、アンインストール時に削除されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS:trackLocation)**

   現在の XY 座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS:trackLifetime &#x200B; ValueIncrease)**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed ActionStart(&#x200B;winJS:trackTimed ActionStart&#x200B;)**

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
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed ActionUpdate (&#x200B;winJS:trackTimed ActionUpdate&#x200B;)**

   `contextData` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。渡された `data` は、特定のアクションの既存のデータに追加され、同じキーが既に `action` に定義されている場合は、データを上書きします。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync (winJS:trackTimedActionExistsAsync)**

   指定した時間計測アクションが存在する場合は true を返し、存在しない場合は false を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
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
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS:clearTrackingQueue)**

   Analytics トラッキングキューから保存されているすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void ClearTrackingQueue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS:getQueueSizeAsync)**

   現在 Analytics キューに保存されているヒット数を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
