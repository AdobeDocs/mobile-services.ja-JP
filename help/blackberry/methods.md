---
description: BlackBerry ライブラリが提供するクラスおよびメソッド。
seo-description: BlackBerry ライブラリが提供するクラスおよびメソッド。
seo-title: Adobe Mobileクラスとメソッドリファレンス
title: Adobe Mobileクラスとメソッドリファレンス
uuid: 1e42d759- be43-4bb3- ac1a- c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

BlackBerry ライブラリが提供するクラスおよびメソッド。

SDKは現在、Adobe Analyticsをサポートしており、メソッドはソリューションに基づく個別のクラスにあります。

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * ADBMobilePrivacyStatusOptIn - ヒットが即座に送信されます。
   * ADBMobilePrivacyStatusOptOut - ヒットは破棄されます。
   * ADBMobilePrivacyStatusUnknown - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

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

   * `ADBMobilePrivacyStatusOptIn` - ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut` - ヒットは破棄されます。
   * `ADBMobilePrivacyStatusUnknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

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

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、[ライフサイクル指標](/help/blackberry/metrics.md)を参照してください。

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

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

これらの各メソッドを使用して、Adobe Analytics レポートスイートにデータを送信します。

* **trackState**

   オプションのコンテキストデータでアプリ状態を追跡します。状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

   >[!TIP]
   >
   >これはページビュー数が増える唯一のトラッキング呼び出しです。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   アプリのアクションを追跡します。アクションとは、アプリ内で測定対象となる重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   現在の XY 座標を送信します。イベントを、サブスクライバーから BPS に受信されるイベントに置き換えます。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` configファイルリファレンス {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json` ファイルを *assets* フォルダーに配置する必要があります。

* **rsids**

   （必須）Analytics データを受け取るための 1 つまたは複数のレポートスイート。レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   以下に、この変数のコードサンプルを示します。

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   （必須）Analytics サーバー。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. プロトコルプレフィックスは、`ssl` 変数に基づいてライブラリで自動的に処理されます。`ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). デフォルト値は `false` です。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうか判断できない場合は、エンタープライズサポートに [お問い合わせ](https://helpx.adobe.com/contact/enterprise-support.ec.html)ください。

   現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、`s.timestamp` 変数を使用するすべての JavaScript ヒットにカスタムタイムスタンプを含めます。

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリケーションの起動が新しいセッションであると見なされるまでの経過時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   キューに格納されるオフラインヒットの最大数。デフォルト値は0（制限なし）です。

* **privacyDefault**

   * `optedin` - ヒットは即座に送信されます。
   * `optedout` - ヒットは破棄されます。
   * `optunknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   この変数は初期値のみを設定します。この値をコードで設定または変更した場合、値が変更されるか、アプリがアンインストールされて再インストールされるまで、新しい値が使用されます。

   デフォルト値は `optedin` です。

`ADBMobileConfig.json` ファイルの例を次に示します。

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
