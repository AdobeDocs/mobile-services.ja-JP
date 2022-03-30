---
description: ADBMobile JSON 設定ファイルを使用する際に役立つ情報を紹介します。
solution: Experience Cloud Services,Analytics
title: ADBMobileConfig.json config
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 42%

---

# ADBMobileConfig.json 設定ファイル {#adbmobileconfig-json-config}

ADBMobile JSON 設定ファイルを使用する際に役立つ情報を紹介します。

SDK は現在、Analytics、Target、Audience Managerなど、複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。設定メソッドの場合、プレフィックスは「Config」です。

* **rsids**

   (**Analytics で必要**) Analytics データを受け取る 1 つ以上のレポートスイート。 レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   * このメソッドの構文を次に示します。

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Analytics と Audience Management で必要**) をクリックします。 親ノードに基づく、Analytics または Audience Management サーバー。 この変数は、`"https://"` または `"https://"` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プロトコルプレフィックスは、 `ssl` 変数を使用します。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。 この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。詳しくは、 [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=ja) 変数に関する情報をAdobe Analyticsドキュメントで参照してください。

* **ssl**

   有効 (`true`) または無効 (`false`)SSL (`HTTPS`) をクリックします。 デフォルト値は `false` です。

* **offlineEnabled**

   有効な場合 (`true`) のヒットは、デバイスがオフラインの間、キューに格納され、後でデバイスがオンラインになったときに送信されます。 オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   レポートスイートでタイムスタンプが有効になっている場合、 `offlineEnabled` 設定プロパティ *必須* は `true`. レポートスイートでタイムスタンプが有効になっていない場合、 `offlineEnabled` 設定プロパティ *必須* は `false`.

   このプロパティを適切に設定しなければ、データが失われます。レポートスイートでタイムスタンプが有効になっているかどうかがわからない場合は、カスタマーケアにお問い合わせください。 現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、 `s.timestamp` 変数を使用します。

   デフォルト値は `false` です。

* **lifecycleTimeout**

   アプリケーションが起動されてから、新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   デフォルト値は 300 秒です。

* **batchLimit**

   ヒットを一括で送信します。

   例えば、 `50`、ヒットは 50 個が保存されるまでキューに登録され、キューに登録されているすべてのヒットが送信されます。 必要 `offlineEnabled=true`の場合、デフォルト値は `0` （バッチ処理なし）。

* **privacyDefault**

   オプションは以下のとおりです。

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown` ：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。 レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      これはデフォルト値のみを設定します。 この値がコードで設定または変更された場合、コードで設定された値はローカルストレージに保存され、変更されるまで使用されるか、アプリがアンインストールされて再インストールされます。

      デフォルト値は `optedin` です。

* **poi**

   各 POI 配列は、対象の地点の POI 名、緯度、経度、半径（メートル単位）を保持します。POI 名には任意の文字列を使用できます。`trackLocation` 呼び出しの送信時に、現在の座標が定義した POI 内にある場合は、コンテキストデータ変数に値が代入され、`trackLocation` 呼び出しで送信されます。

   * この変数のコードサンプルを次に示します。

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Target で必須**) 割り当てられたクライアントコード。

* **timeout**

   ターゲットが応答を待つ時間を決定します。

次に、 `ADBMobileConfig.json` ファイル：

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
