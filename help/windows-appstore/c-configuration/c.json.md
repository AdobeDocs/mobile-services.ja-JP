---
description: ADBMobile JSON 設定ファイルを使用する際に役立つ情報です。
seo-description: ADBMobile JSON 設定ファイルを使用する際に役立つ情報です。
seo-title: ADBMobileConfig.json設定ファイル
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json設定ファイル
topic: 開発者と導入
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` 設定ファイル {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

現在、SDK では、Analytics、Target、Audience Manager をはじめとする複数の Adobe Experience Cloud ソリューションがサポートさています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。設定メソッドには「Config」というプレフィックスが付けられています。

* **rsids**

   （Analytics の場合は必須）：Analytics データを受け取るための 1 つまたは複数のレポートスイート。レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   * この変数のコード例を次に示します。

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   （Analytics および Audience Management の場合は必須）：親ノードに基づく、Analytics または Audience Management サーバー。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. プロトコルプレフィックスは、`ssl` 変数に基づいてライブラリで自動的に処理されます。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). デフォルト値は `false` です。

* **offlineEnabled**

   有効（true）にした場合、ヒットはデバイスがオフラインのときにキューに格納され、後でデバイスがオンラインになったときに送信されます。オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうか判断できない場合は、カスタマーケアにお問い合わせください。現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、`s.timestamp` 変数を使用するすべての JavaScript ヒットにカスタムタイムスタンプを含めます。

* **lifecycleTimeout**

   アプリケーションの起動が新しいセッションであると見なされるまでの経過時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。デフォルト値は 300 秒です。

* **batchLimit**

   ヒットのバッチ送信を有効にします。例えば、この変数を 50 に設定すると、キューに格納されているヒットの数が 50 に達したときに、キュー内のすべてのヒットが一括で送信されます。が必要で `offlineEnabled=true`す。 The default value is `0` (No batching).

* **privacyDefault**

   * `optedin`  — ヒットは直ちに送信されます。
   * `optedout` - hits are discarded.
   * `optunknown` - レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      デフォルト値は `optedin` です。

      >[!TIP]
      >
      >This sets the default value only. この値がコード内で設定または変更された場合、値が再び変更されるか、アプリがアンインストールされて再インストールされるまで、コードによって設定された値がローカルストレージに保存されて使用され続けます。

* **poi**

   各 POI 配列は、対象の地点の POI 名、緯度、経度、半径（メートル単位）を保持します。POI 名には任意の文字列を使用できます。`trackLocation` 呼び出しの送信時に、現在の座標が定義した POI 内にある場合は、コンテキストデータ変数に値が代入され、`trackLocation` 呼び出しで送信されます。

   * この変数のコード例を次に示します。

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Target が応答を待つ時間を決定します。

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

