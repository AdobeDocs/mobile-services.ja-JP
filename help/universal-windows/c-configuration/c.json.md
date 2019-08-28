---
description: ADBMobile JSON 設定ファイルを使用する際に役立つ情報です。
seo-description: ADBMobile JSON 設定ファイルを使用する際に役立つ情報です。
seo-title: ADBMobileConfig. json config
solution: Marketing Cloud、Analytics
title: ADBMobileConfig. json config
topic: 開発者と導入
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobileConfig. json設定ファイル {#adbmobileconfig-json-config}

ADBMobile JSON 設定ファイルを使用する際に役立つ情報です。

現在、SDK では、Analytics、Target、Audience Manager をはじめとする複数の Adobe Experience Cloud ソリューションがサポートさています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。設定メソッドには「Config」というプレフィックスが付けられています。

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   * このメソッドの構文を次に示します。

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Required by Analytics and Audience Management**). 親ノードに基づく、Analytics または Audience Management サーバー。This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. プロトコルプレフィックスは、`ssl` 変数に基づいてライブラリで自動的に処理されます。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). デフォルト値は `false` です。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   このプロパティを適切に設定しなければ、データが失われます。レポートスイートでタイムスタンプが有効になっているかどうかが不明な場合は、カスタマーケアにお問い合わせください。If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリケーションの起動が新しいセッションであると見なされるまでの経過時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   ヒットのバッチ送信を有効にします。

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. デフォルト `offlineEnabled=true`値で、デフォルト値は `0` （バッチ処理なし）です。

* **privacyDefault**

   オプションは以下のとおりです。

   * `optedin` - ヒットは即座に送信されます。
   * `optedout` - ヒットは破棄されます。
   * `optunknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      これにより、デフォルト値のみが設定されます。この値がコード内で設定または変更された場合、値が再び変更されるか、アプリがアンインストールされて再インストールされるまで、コードによって設定された値がローカルストレージに保存されて使用され続けます。

      デフォルト値は `optedin` です。

* **poi**

   各 POI 配列は、対象の地点の POI 名、緯度、経度、半径（メートル単位）を保持します。POI 名には任意の文字列を使用できます。`trackLocation` 呼び出しの送信時に、現在の座標が定義した POI 内にある場合は、コンテキストデータ変数に値が代入され、`trackLocation` 呼び出しで送信されます。

   * 以下に、この変数のコードサンプルを示します。

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   ターゲットが応答を待つ時間を決定します。

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
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
