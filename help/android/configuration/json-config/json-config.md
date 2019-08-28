---
description: この情報は、ADBMobile.json 設定ファイルを使用する場合に役立ちます。
seo-description: この情報は、ADBMobile.json 設定ファイルを使用する場合に役立ちます。
seo-title: ADBMobile JSON 設定
solution: Marketing Cloud、Analytics
title: ADBMobile JSON 設定
topic: 開発者と導入
uuid: 1decf605-7bc3-4e73- ad52-1prop5821599e
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobile JSON config file {#adbmobile-json-config}

この情報は、ADBMobile. json設定ファイル内の変数を理解するのに役立ちます。

## `ADBMobileConfig.json` configファイルリファレンス {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

複数のプラットフォームで同じ設定ファイルをアプリに使用することができます。

>[!TIP]
>
>**Android**&#x200B;では、ファイルを `ADBMobileConfig.json``assets` フォルダー内に配置する必要があります。

以下に、JSONファイル内の変数と各変数に必要な最小SDKバージョンのリストを示します。

* **獲得**
   * 最小 SDK バージョン：4.1
   * モバイルアプリの獲得を有効にします。
      * `server`：最初の起動時に獲得リファラーの確認がおこなわれる獲得サーバー。
      * `appid`：獲得サーバー上でこのアプリを一意に識別する、生成された ID。
   このセクションがない場合は、モバイルアプリの獲得を有効にし、SDK 設定ファイルを再度ダウンロードします。詳しくは、この変数のリストの *referentTimeout* を参照してください。

* **analyticsForwardingEnabled**
   * 最小SDKバージョンは4.8.0です。
   * デフォルト値は `false` です。

      `audienceManager` オブジェクトのプロパティ。Audience Manager が設定され、`analyticsForwardingEnabled` が `true` に設定されている場合、すべての Analytics トラフィックも Audience Manager に転送されます。

* **backdateSessionInfo**
   * 最小 SDK バージョン：4.6.
   * Adobe SDK がセッション情報のヒットの日付を遡る機能を有効または無効にします。

      セッション情報のヒットは、現在、クラッシュ回数とセッションの長さで構成されており、有効または無効にできます。

      **ヒットの有効化または無効化**

      * 値が `false` に設定されている場合、ヒットは&#x200B;**無効**&#x200B;になります。SDK は 4.1 より前の動作に戻り、前のセッションのセッション情報を後続セッションの最初のヒットとまとめて処理します。また、Adobe SDK は、セッション情報を現在のライフサイクルに付加し、これにより、訪問の水増しを防ぎます。水増し訪問が発生しなくなるので、すぐに訪問回数が減少します。

      * 値を指定しない場合、デフォルト値は `true` になり、ヒットは&#x200B;**有効**&#x200B;になります。ヒットを有効にした場合、Adobe SDK は、セッション情報のヒットを前のセッションの最終ヒットの 1 秒後に戻します。これによって、クラッシュとセッションのデータが、その正しい発生日に関連付けられます。1 つの副作用として、日付を遡ったヒットの訪問が SDK によって作成される可能性があります。アプリケーションを新しく起動するたびに、1 つのヒットの日付を遡ります。

         >[!IMPORTANT]
         >
         >バックグラウンドセッションのヒット情報がセッション情報サーバ呼び出しで送信され、追加のサーバーコールが適用される場合があります。

* **batchLimit**
   * 最小 SDK バージョン：4.1
   * 連続する呼び出しで送信されるヒット数のしきい値。

      例えば、この `batchLimit` を 10 に設定した場合は、ヒットが 10 個たまるまでヒットをキューに格納していきます。10 番目のヒットが格納されると、10 個のヒットすべてが連続して送信されます。

      次の情報に留意してください。

      * デフォルト値は `0` です。これはバッチ処理が有効になっていないことを意味します。
      * 必要 `offlineEnabled = true`です。

* **charset**
   * 最小 SDK バージョン：4.0
   * Analytics に送信されるデータに使用する文字セットを定義します。

      この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。

* **clientCode**
   * 最小 SDK バージョン：4.0
   * 割り当てたクライアントコード。

      >[!IMPORTANT]
      >
      >この変数は、Targetで必須です。

* **coopUnsafe**
   * 最小 SDK バージョン：4.16.1
   * `marketingCloud` オブジェクトのブールプロパティ。このプロパティを設定すると、デバイスがExperience `true`CloudのDevice Co- opをオプトアウトする原因となります。
   * Default value is `false`.
   * この設定は、Device Co-op をプロビジョニングしたユーザー&#x200B;**にのみ**&#x200B;適用されます。
   Device Co-op のユーザーで、この値を `true` に設定する必要がある場合は、Co-op グループに連絡して、お使いの Device Co-op アカウント上でブラックリストフラグをリクエストする必要があります。これらのフラグをセルフサービスで有効にする方法はありません。

   次の情報に留意してください。

   * When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
   * If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.


* **environmentId**
   * 最小 SDK バージョン：4.14
   * 使用する環境の ID です。

      有効な ID（`environmentId=8`）を指定できます。`environmentId` が含まれていない場合、デフォルトの実稼動環境を使用します。

* **lifecycleTimeout**
   * 最小 SDK バージョン：4.0
   * デフォルト値は 300 秒です。

      アプリケーションが起動されてから新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。

      アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

* **messages**

   * 最小 SDK バージョン：4.2
   * Adobe Mobile Services によって自動的に生成され、アプリ内メッセージの設定を定義します。詳しくは、以下の「*メッセージの説明*」節を参照してください。

* **offlineEnabled**

   * 最小 SDK バージョン：4.0
   * 有効にした場合、ヒットはデバイスがオフラインのときにキューに格納され、後でデバイスがオンラインになったときに送信されます。

      オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。

      デフォルト値は `false` です。

      >[!IMPORTANT]
      >
      >レポートスイートでタイムスタンプが有効になっている場合、`offlineEnabled` 設定プロパティを&#x200B;**必ず** true に設定してください。レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;**必ず** false に設定してください。
      >
      >このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうか判断できない場合は、カスタマーケアに問い合わせるか、Adobe Mobile Services から設定ファイルをダウンロードしてください。

      現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、`s.timestamp` 変数を使用するすべての JavaScript ヒットにカスタムタイムスタンプを含めます。

* **org**

   * 最小 SDK バージョン：4.3
   * ID サービスの Experience Cloud 組織 ID を指定します。

* **poi**
   * 最小 SDK バージョン：4.0
   * 各目標地点（POI）配列は、対象の地点の POI 名、緯度、経度および半径（メートル単位）を保持します。

      POI 名には任意の文字列を使用できます。`trackLocation` 呼び出しの送信時に、現在の座標が定義した POI 内にある場合は、コンテキストデータ変数に値が代入され、`trackLocation` 呼び出しで送信されます。

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      バージョン 4.2 以降、POI は Adobe Mobile インターフェイスで定義され、アプリ設定ファイルに動的に同期されます。この同期をおこなうには、`analytics.poi` 設定が必要です。

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      これを設定しない場合は、`ADBMobile.json` ファイルを更新してこの行を含める必要があります。更新された設定ファイルをダウンロードするには、「開始する前に」を [](/help/android/getting-started/requirements.md)参照してください。

* **postback**
   * 最小 SDK バージョン：4.6
   * 「コールバック」メッセージテンプレートの定義を次に示します。

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      The `payload` object in the code is a sample payload for a message definition that goes in the `ADBMobileConfig.json` file. For more information, see [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * 最小 SDK バージョン：4.0
   * デフォルト値は `optedin` です。
      * `optedin`：ヒットは即座に送信されます。
      * `optedout`：ヒットは破棄されます。
      * `optunknown`：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。
      If your report suite is not timestamp-enabled, hits are discarded until the privacy status changes to `optedin`.  これは初期値を設定するだけです。この値をコードで設定または変更した場合、値が再び変更されるか、アプリがアンインストールされて再インストールされるまで、新しい値が使用されます。


* **referrerTimeout**
   * 最小 SDK バージョン：4.1
   * SDK が最初の起動時にタイムアウトするまでに獲得リファラーデータを待機する秒数。獲得を使用している場合は、5 秒のタイムアウトをお勧めします。

      >[!IMPORTANT]
      >
      >この変数は、獲得で必要です。この変数を `0` に設定するか含めない場合、SDK は獲得データを待機せず、獲得指標は追跡されません。

* **remotes**
   * 最小 SDK バージョン：4.2
   * 自動的に設定され、アドビがホストする、動的設定ファイルのエンドポイントを定義します。

      起動するたびに各設定ファイルの最終更新時間が現在のバージョンと比較され、更新がダウンロードされて保存されます。
      * `analytics.poi` は、ホストされる POI 設定のエンドポイントです。
      * `messages` は、ホストされるアプリ内メッセージ設定のエンドポイントです。

* **rsids**
   * 最小 SDK バージョン：4.0
   * Analytics データを受け取るための 1 つまたは複数のレポートスイート。レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >この変数は、Analyticsで必要です。

* **server**
   * 最小 SDK バージョン：4.0
   * 親ノードに基づく、Analytics または Audience Management サーバー。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. プレフィックスは、ライブラリによって自動的に処理され、`ssl` 変数に基づきます。`ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

* **ssl**
   * 最小 SDK バージョン：4.0
   * デフォルト値は `false` です。

      SSL（HTTPS）を使用して測定データを送信する機能を有効（`true`）または無効（`false`）にします。

      「コールバック」メッセージテンプレートの定義を次に示します。

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * 最小 SDK バージョン：4.0
   * Target が応答を待つ時間を決定します。


## Sample `ADBMobileConfig.json` file {#section_4655EF79744649E5A5AE19E3224C472C}

サンプルの `ADBMobileConfig.json` ファイルを次に示します。

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## メッセージの説明 {#section_B97D654BA92149CE91F525268D7AD71F}

メッセージノードは Adobe Mobile Services によって自動的に生成されるので、通常は手動で変更する必要がありません。次の説明は、トラブルシューティングの目的で提供されています。

* "messageId"
* 生成された ID。必須
* "template"
   * "alert"、"fullscreen" または "local"
   * 必須

* "showOffline"
   * true または false
   * デフォルトは false です。

* "showRule"
   * "always"、"once" または "untilClick"
   * 必須

* "endDate"
   * 1970 年 1 月 1 日からの経過秒数
   * デフォルトは 2524730400 です。

* "startDate"
   * 1970 年 1 月 1 日からの経過秒数
   * デフォルトは 0 です。

* "payload"
   * "html"
      * フルスクリーンテンプレートのみ。必須
      * メッセージを定義する html
   * "image"
      * フルスクリーンのみ。オプション
      * フルスクリーン画像に使用する画像の URL
   * "altImage"
      * フルスクリーンのみ。オプション
      * バンドルされた画像の名前（
         * image
         *  に指定された URL に到達できない場合に使用）
   * "title"
      * フルスクリーンおよび警告。必須
      * フルスクリーンまたは警告メッセージのタイトルテキスト
   * "content"
      * 警告およびローカル通知。必須
      * 警告メッセージのサブテキスト、またはローカル通知メッセージの通知テキスト
   * "confirm"
      * 警告。オプション
      * 確認ボタンに使用されるテキスト
   * "cancel"
      * 警告。必須
      * キャンセルボタンに使用されるテキスト
   * "url"
      * 警告。オプション
      * 確認ボタンがクリックされたときにロードする URL アクション
   * "wait"
      * ローカル通知。必須
      * 条件に一致してからローカル通知を転送するまでの待機時間（秒数）



* 「audiences」
   * メッセージの表示方法を定義するオブジェクトの配列
   * 「key」
      * ヒット内で検索する変数名。必須
* 「matches」
   * 比較時に使用するマッチャーのタイプ
   * eq = 次の値と等しい
   * ne = 次の値と等しくない
   * co = 次の値を含む
   * nc = 次の値を含まない
   * sw = 次の値で始まる
   * ew = 次の値で終わる
   * ex = 次の値が存在する
   * nx = 次の値が存在しない
   * lt = 次の値より小さい
   * le = 次の値以下
   * gt = 次の値を超える
   * ge = 次の値以上
* 「values」
   * matches に指定されたマッチャータイプに基づいて 
      * key
      * と以下に指定されたマッチャ―タイプ
      * matches
* 「trigger」
   * audiences と同じですが、オーディエンスではなくアクションです。
   * 「key」
   * 「matches」
   * 「values」
