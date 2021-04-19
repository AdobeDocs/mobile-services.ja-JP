---
description: ADBMobile JSON設定ファイルの使用に役立つ情報です。
seo-description: ADBMobile JSON設定ファイルの使用に役立つ情報です。
seo-title: ADBMobileConfig.json設定ファイル
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json設定ファイル
topic-fix: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
exl-id: 520dffb8-ca47-444f-bbc9-f18413ddeb05
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 44%

---

# `ADBMobileConfig.json` 設定ファイル  {#adbmobileconfig-json-config}

`ADBMobile.json` configファイルを使用する際に役立つ情報です。

SDKは、現在、Analytics、ターゲット、Audience Managerを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。設定メソッドの先頭に「Config」が付きます。

* **rsids**

   （Analyticsで必須）Analyticsデータを受け取るための1つ以上のレポートスイート。 レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   * この変数のコードサンプルを次に示します。

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Analyticsおよびオーディエンス管理で必須)。 親ノードに基づくAnalyticsまたはオーディエンス管理サーバー。 この変数は、`https://` または `https://` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プロトコルプレフィックスは、`ssl`変数に基づいてライブラリによって自動的に処理されます。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **charset**

   Analyticsに送信されるデータに使用する文字セットを定義します。 この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。詳しくは、「[s.charSet](https://docs.adobe.com/content/help/ja-JP/analytics/implementation/vars/config-vars/charset.html)」を参照してください。

* **ssl**

   SSL (HTTPS)を介して測定データを送信する設定を、有効(`true`)または無効(`false`)にします。 デフォルト値は `false` です。

* **offlineEnabled**

   有効(true)に設定すると、デバイスがオフラインの間、ヒットはキューに登録され、デバイスがオンラインの間、後で送信されます。 オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

   >[!IMPORTANT]
   >
   >レポートスイートでタイムスタンプが有効になっている場合、`offlineEnabled`設定プロパティ&#x200B;*は*&#x200B;をtrueに設定する必要があります。 レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうかが不明な場合は、カスタマーケアにお問い合わせください。 現在、JavaScriptからもデータを収集するレポートスイートにAppMeasurementデータをレポートしている場合は、モバイルデータ用に個別のレポートスイートを設定するか、`s.timestamp`変数を使用してすべてのJavaScriptヒットにカスタムタイムスタンプを含める必要があります。

* **lifecycleTimeout**

   アプリケーションが起動されてから、新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。デフォルト値は 300 秒です。

* **batchLimit**

   ヒットをバッチで送信します。 例えば、50に設定した場合、50件のヒットが格納されるまでキューに登録され、キューに登録されたすべてのヒットが送信されます。 `offlineEnabled=true` が必要です。デフォルト値は`0`です（バッチ処理なし）。

* **privacyDefault**

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown`  — レポートスイートでタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      デフォルト値は `optedin` です。

      >[!TIP]
      >
      >これにより、デフォルト値のみが設定されます。 この値がコード内で設定または変更された場合、コードによって設定された値はローカルストレージに保存され、変更されるまで使用されます。または、アプリがアンインストールされてから再インストールされます。

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

   (**ターゲット**&#x200B;に必須)割り当てられたクライアントコード。

* **timeout**

   Target が応答を待つ時間を決定します。

次に`ADBMobileConfig.json`ファイルの例を示します。

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
