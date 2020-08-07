---
description: BlackBerryライブラリが提供するクラスとメソッド。
seo-description: BlackBerryライブラリが提供するクラスとメソッド。
seo-title: AdobeMobileクラスおよびメソッドの参照
title: AdobeMobileクラスおよびメソッドの参照
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 54%

---


# AdobeMobileクラスおよびメソッドの参照 {#adobe-mobile-class-and-method-reference}

BlackBerryライブラリが提供するクラスとメソッド。

SDKは現在、Adobe Analyticsをサポートしており、メソッドはソリューションに基づいて別々のクラスにあります。

## SDK設定 {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * ADBMobilePrivacyStatusOptIn — ヒットは即座に送信されます。
   * ADBMobilePrivacyStatusOptOut — ヒットは破棄されます。
   * ADBMobilePrivacyStatusUnknown — レポートスイートでタイムスタンプが有効な場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

   * このメソッドの構文を次に示します。

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   現在のユーザーのプライバシーステータスを `status` に設定します。次のいずれかの値に設定します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown`  — レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   カスタム識別子が設定されている場合は、ユーザー識別子を返します。Returns `null` if a custom identifier is not set. デフォルト値は `null` です。

   * このメソッドの構文を次に示します。

      ```cpp
      static QString getUserIdentifier();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドの構文を次に示します。

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   現在のデバッグログの環境設定を返します。デフォルト値は `false` です。

   * このメソッドの構文を次に示します。

      ```cpp
      static bool getDebugLogging();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   デバッグログの環境設定を `debugLogging` に設定します。

   * このメソッドの構文を次に示します。

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、「[ライフサイクル指標](/help/blackberry/metrics.md)」を参照してください。

   * このメソッドの構文を次に示します。

      ```cpp
      static void collectLifecycleData();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics メソッド {#section_91F4AD0A045D4E4E8F9A93450503E49E}

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

* **trackState**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態は、「ホームダッシュボード」、「アプリ設定」、「カート」など、アプリで使用できる表示です。 これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   アプリのアクションを追跡します。アクションとは、「ログオン」、「バナーのタップ」、「フィード購読」など、測定対象のアプリで発生する操作です。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   現在の XY 座標を送信します。イベントを、サブスクライバからBPSに受信したイベントに置き換えます。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 設定ファイルのリファレンス {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   （必須）Analyticsデータを受け取る1つ以上のレポートスイート。 レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   この変数のコード例を次に示します。

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必須). Analyticsサーバー。 この変数は、`https://` または `https://` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プロトコルのプレフィックスは、 `ssl` 変数に基づいてライブラリによって自動的に処理されます。 `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analyticsに送信されるデータに使用する文字セットを定義します。 この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。

* **ssl**

   SSL(HTTPS)を介して測定データを送信する設定を、有効(`true`)または無効(`false`)にします。 デフォルト値は `false` です。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうかが不明な場合は、 [エンタープライズサポート](https://helpx.adobe.com/jp/contact/enterprise-support.ec.html)にお問い合わせください。

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリが起動してからその起動が新しいセッションと見なされるまでに経過する必要がある時間（秒単位）を指定します。 このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   キューに格納されるオフラインヒットの最大数。 デフォルト値は0（制限なし）です。

* **privacyDefault**

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown`  — レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。

      レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   この変数は、初期値のみを設定します。 この値がコード内で設定または変更された場合、新しい値が変更されるまで使用されるか、アプリケーションがアンインストールおよび再インストールされます。

   デフォルト値は `optedin` です。

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
