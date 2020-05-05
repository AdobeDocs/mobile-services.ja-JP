---
description: ADBMobile JSON設定ファイルの使用に役立つ情報です。
seo-description: ADBMobile JSON設定ファイルの使用に役立つ情報です。
seo-title: ADBMobileConfig.json config
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json config
topic: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# ADBMobileConfig.json config file {#adbmobileconfig-json-config}

ADBMobile JSON設定ファイルの使用に役立つ情報です。

SDKは、現在、Analytics、ターゲット、オーディエンスマネージャーを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。設定メソッドの先頭に「Config」が付きます。

* **rsids**

   (Analytics **で必須**)Analyticsデータを受け取るための1つ以上のレポートスイート。 複数のレポートスイートIDは、スペースを入れずにコンマで区切る必要があります。

   * このメソッドの構文を次に示します。

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Analyticsおよびオーディエンス管理で&#x200B;**必須**)。 親ノードに基づくAnalyticsまたはオーディエンス管理サーバー。 この変数は、`"https://"` または `"https://"` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プロトコルのプレフィックスは、 `ssl` 変数に基づいてライブラリによって自動的に処理されます。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analyticsに送信されるデータに使用する文字セットを定義します。 この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。詳しくは、「[s.charSet](https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/charset.html)」を参照してください。

* **ssl**

   SSLを介して測定データを送信する設定を、有効(`true`)または無効(`false`)にし`HTTPS`ます()。 デフォルト値は `false` です。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   この設定が正しく行われないと、データが失われます。 レポートスイートでタイムスタンプが有効になっているかどうかがわからない場合は、カスタマーケアにお問い合わせください。 If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリが起動してからその起動が新しいセッションと見なされるまでに経過する必要がある時間（秒単位）を指定します。 このタイムアウトは、アプリケーションがバックグラウンドに送信され、再びアクティブになる場合にも適用されます。 アプリがバックグラウンドに従っている時間は、セッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   ヒットをバッチで送信します。

   例えば、に設定した場合、50件のヒットが格納されるまでキューに入れられ、 `50`その後、キューに入れられたすべてのヒットが送信されます。 が必要 `offlineEnabled=true`で、デフォルト値は `0` （バッチ処理なし）です。

* **privacyDefault**

   オプションは以下のとおりです。

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown`  — レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      これにより、デフォルト値のみが設定されます。 この値がコード内で設定または変更された場合、コードによって設定された値はローカルストレージに保存され、変更されるまで使用されます。または、アプリがアンインストールされてから再インストールされます。

      デフォルト値は `optedin` です。

* **poi**

   各 POI 配列は、対象の地点の POI 名、緯度、経度、半径（メートル単位）を保持します。POI 名には任意の文字列を使用できます。`trackLocation` 呼び出しの送信時に、現在の座標が定義した POI 内にある場合は、コンテキストデータ変数に値が代入され、`trackLocation` 呼び出しで送信されます。

   * この変数のコード例を次に示します。

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**ターゲットが必要**)割り当てたクライアントコード。

* **timeout**

   ターゲットが応答を待機する時間を指定します。

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
