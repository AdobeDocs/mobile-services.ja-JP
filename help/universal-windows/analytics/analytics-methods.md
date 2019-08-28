---
description: Universal Windows Platform SDK を Adobe Analytics で使用する際に役立つ情報です。
seo-description: Universal Windows Platform SDK を Adobe Analytics で使用する際に役立つ情報です。
seo-title: Analyticsのメソッド
solution: Marketing Cloud、Analytics
title: Analyticsのメソッド
topic: 開発者と導入
uuid: cc299bb5- ec61-49bf-869a- f3c3bc83359f
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Universal Windows Platform SDK を Adobe Analytics で使用する際に役立つ情報です。

現在、SDK では、Analytics、Target、Audience Manager をはじめとする複数の Adobe Experience Cloud ソリューションがサポートさています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。Analytics メソッドには「Analytics」というプレフィックスが付けられています。

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **trackState（winJS:trackState）**

   オプションのコンテキストデータでアプリ状態を追跡します。状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。これらの状態は Web サイト上のページによく似ており、`TrackState` コールはページビュー数を増分します。`state` が空の場合は、レポートに「app name app version (build)」と表示されます。レポートにこの値がある場合、各 `state` 呼び出しで `TrackState` を設定していることを確認してください。

   >[!TIP]
   >
   >これはページビュー数が増える唯一のトラッキング呼び出しです。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **trackAction（WinJS:trackAction）**

   アプリのアクションを追跡します。アクションとは、アプリ内で測定対象となる重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

   * このメソッドの構文を次に示します。

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **getTrackingIdentifierAsync（winJS:getTrackingIdentifierAsync）**

   Analytics 用に自動的に生成された訪問者 ID を返します。これは、初回起動時に生成され、それ以降、保存および使用されるアプリ固有の一意の訪問者 ID です。この ID は、アプリがアップグレードされても保持されますが、アンインストール時には削除されます。

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

* **trackLocation（winJS:trackLocation）**

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

* **trackLifetimeValueIncrement（winJS:trackLifetimeValueIncrement）**

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

* **trackTimedActionStart（WinJS:TrackTimedActionStart）**

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

* **trackTimedActionUpdate（WinJS:TrackTimedActionUpdate）**

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

* **trackTimedActionExistsAsync（WinJS:TrackTimedActionExistsAsync）**

   指定された時間計測アクションが存在する場合はtrue、存在しない場合はfalseを返します。

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

* **trackTimedActionEnd（WinJS:TrackTimedActionEnd）**

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

* **clearTrackingQueue（winJS:ClearTrackingQueue）**

   Analytics 追跡キューに格納されているすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void ClearTrackingQueue();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **getQueueSizeAsync（winJS:getQueueSizeAsync）**

   現在 Analytics キューに格納されているヒットの数を返します。

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
