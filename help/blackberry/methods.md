---
description: BlackBerry ライブラリが提供するクラスとメソッド。
title: Adobe Mobile クラスおよびメソッドの参照
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
exl-id: ad73ec1d-d082-4237-b7cb-b8ec2f7595a3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 58%

---

# Adobe Mobile クラスおよびメソッドの参照 {#adobe-mobile-class-and-method-reference}

BlackBerry ライブラリが提供するクラスとメソッド。

SDK は現在、Adobe Analyticsをサポートしています。メソッドは、ソリューションに基づいて別々のクラスにあります。

## SDK 設定 {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   現在のユーザーのプライバシーステータスの enum 表現を返します。

   * ADBMobilePrivacyStatusOptIn — ヒットは即座に送信されます。
   * ADBMobilePrivacyStatusOptOut — ヒットは破棄されます。
   * ADBMobilePrivacyStatusUnknown — レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

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
   * `ADBMobilePrivacyStatusUnknown` ：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   カスタム識別子が設定されている場合は、ユーザー識別子を返します。カスタム識別子が設定されていない場合は `null` を返します。 デフォルト値は `null` です。

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

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、「home dashboard」、「app settings」、「cart」など、アプリで使用可能なビューです。 これらの状態は Web サイト上のページによく似ており、`trackState` コールにより、ページビュー数が増分されます。

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

   アプリのアクションを追跡します。アクションとは、アプリ内で測定に価する重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   現在の XY 座標を送信します。イベントを、サブスクライバから BPS に受信したイベントで置き換えます。

   * このメソッドの構文を次に示します。

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 設定ファイルのリファレンス {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json` ファイルは、*assets* フォルダーに配置する必要があります。

* **rsids**

   （必須）Analytics データを受け取る 1 つ以上のレポートスイート。 レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   この変数のコードサンプルを次に示します。

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必須). Analytics サーバー。 この変数は、`https://` または `https://` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プロトコルプレフィックスは、 `ssl` 変数に基づいて、ライブラリによって自動的に処理されます。 `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。 この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。

* **ssl**

   SSL(HTTPS) を介した測定データの送信を有効 (`true`) または無効 (`false`) にします。 デフォルト値は `false` です。

* **offlineEnabled**

   有効 (`true`) にすると、ヒットはデバイスがオフラインの間キューに入れられ、デバイスがオンラインの間後で送信されます。 オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   >[!TIP]
   >
   >レポートスイートでタイムスタンプが有効になっている場合、`offlineEnabled` 設定プロパティ *は `true` である必要があります。*&#x200B;レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうかが不明な場合は、[ エンタープライズサポート ](https://helpx.adobe.com/jp/contact/enterprise-support.ec.html) にお問い合わせください。

   現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、`s.timestamp` 変数を使用してすべての JavaScript ヒットにカスタムタイムスタンプを含めます。

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリケーションが起動されてから、新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   キューに格納されるオフラインヒットの最大数。 デフォルト値は 0（制限なし）です。

* **privacyDefault**

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown` ：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   この変数は、初期値のみを設定します。 この値がコードで設定または変更された場合、新しい値が変更されるまで使用されるか、アプリがアンインストールされて再インストールされるまで使用されます。

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
