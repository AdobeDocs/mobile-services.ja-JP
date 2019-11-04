---
description: Android ライブラリによって提供される Adobe Analytics メソッドのリストを示します。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: Android ライブラリによって提供される Adobe Analytics メソッドのリストを示します。
seo-title: Analytics メソッド
solution: Experience Cloud,Analytics
title: Analytics メソッド
topic: 開発者と導入
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics メソッド{#analytics-methods}

Android ライブラリによって提供される Adobe Analytics メソッドのリストを示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。例えば、Experience Cloud ID メソッドのプレフィックスは、`analytics` です。

次の各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

* **trackState**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、アプリで使用可能なビューのことで、`home dashboard`、`app settings`、`cart` などがあります。これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

   `state` が空の場合、`app name app version (build)` がレポートに表示されます。レポートにこの値がある場合、各 `state` 呼び出しで `trackState` を設定していることを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction**：アプリのアクションを追跡します。

   アプリ内で発生する `logons`、`banner taps`、`feed subscriptions` などのアクションと、その他の指標を測定します。

   * このメソッドの構文を次に示します。

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier**：Analytics 用に自動的に生成された訪問者識別子を返します。

   これは、初回起動時に生成され、それ以降、保存および使用されるアプリ固有の一意の訪問者 ID です。ID は、アプリをアップグレードしても保持され、アプリをアンインストールすると削除されます。

   * このメソッドの構文を次に示します。

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   現在の緯度と経度、および定義済みの目標地点の場所を送信します。詳しくは、「[位置情報と目標地点](/help/android/location/geo-poi.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   `action` という名前の時間計測アクションを開始します。

   既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。
   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   `contextData` を渡して、`action` に関連付けられているコンテキストデータを更新します。渡された `data` は、アクションの既存のデータに追加されます。`action` に対して同じキーが既に定義されている場合は、データが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   時間計測アクションを終了します。`block` を指定する場合は、最終的な時間値にアクセスし、最終ヒットを送信する前に `data` を操作できます。

   >[!TIP]
   >
   >`block` を指定する場合、ヒットを送信するには `true` を返す必要があります。`block` に `null` を渡すと、最終ヒットが送信されます。

   * このメソッドの構文を次に示します。

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **SDK 4.1 が必要です。**

   現在キューに格納されているヒット数にかかわらず、このメソッドは、オフラインキュー内のすべてのヒットを送信することをライブラリに強制します。

   * このメソッドの構文を次に示します。

      ```java
      voidsendQueuedHits()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   オフラインキュー内に格納されているトラッキングコール数を返します。

   * このメソッドの構文を次に示します。

      ```java
      long getQueueSize()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   オフラインキューからすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      voidclearQueue()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > キューを手動でクリアする場合は、注意が必要です。このプロセスを元に戻すことはできません。