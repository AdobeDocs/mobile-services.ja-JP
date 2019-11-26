---
description: この情報は、ADBMobile.json 設定ファイルを使用する場合に役立ちます。
seo-description: この情報は、ADBMobile.json 設定ファイルを使用する場合に役立ちます。
seo-title: ADBMobile JSON 設定
solution: Marketing Cloud,Analytics
title: ADBMobile JSON 設定
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: ht
source-git-commit: bb7fc1c1fc6e88549a1673baedae19f808d222f0

---


# ADBMobile JSON 設定 {#adbmobile-json-config}

この情報は、`ADBMobile.json` 設定ファイルを使用する場合に役立ちます。

## ADBMobileConfig.json 設定ファイルのリファレンス {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

複数のプラットフォームで同じ設定ファイルをアプリに使用することができます。

>[!TIP]
>
>**iOS** では、バンドル内でアクセス可能な任意の場所に `ADBMobileConfig.json` ファイルを配置できます。

* **acquisition**

   モバイルアプリの獲得を有効にします。

   このセクションがない場合は、モバイルアプリの獲得を有効にして、SDK 設定ファイルを再度ダウンロードしてください。詳しくは、以下の *referrerTimeout* を参照してください。

   * `server` - 初回起動時に獲得リファラーを探すために確認される獲得サーバー。
   * `appid` - 獲得サーバー上でこのアプリを一意に識別する生成された ID。
   * 最小 SDK バージョン：4.1

* **analyticsForwardingEnabled**

   `audienceManager` オブジェクトのプロパティ。`Audience Manager` が設定され、`analyticsForwardingEnabled` が `true` に設定されている場合は、Analytics のトラフィックもすべて Audience Manager に転送されます。デフォルト値は `false` です。

   * 最小 SDK バージョン：4.8.0

* **backdateSessionInfo**

   Adobe SDK がセッション情報のヒットの日付を遡る機能を有効または無効にします。

   セッション情報のヒットは、現在、クラッシュ回数とセッションの長さで構成されており、有効または無効にできます。

   * 値が `false` に設定されている場合、ヒットは&#x200B;**無効**&#x200B;になります。

      SDK は 4.1 より前の動作に戻り、前のセッションのセッション情報を後続セッションの最初のヒットとまとめて処理します。また、Adobe SDK は、セッション情報を現在のライフサイクルに付加し、これにより、訪問の水増しを防ぎます。水増し訪問が発生しなくなるので、すぐに訪問回数が減少します。

   * 値を指定しない場合、デフォルト値は `true` になり、ヒットは&#x200B;**有効**&#x200B;になります。

      ヒットを有効にした場合、Adobe SDK は、セッション情報のヒットを前のセッションの最終ヒットの 1 秒後に戻します。これによって、クラッシュとセッションのデータが、その正しい発生日に関連付けられます。1 つの副作用として、日付を遡ったヒットの訪問が SDK によって作成される可能性があります。アプリケーションを新しく起動するたびに、1 つのヒットの日付を遡ります。

   * 最小 SDK バージョン：4.6
   >[!IMPORTANT]
   >
   >日付を遡るセッションヒット情報は、セッション情報サーバー呼び出しで送信されます。このとき、追加のサーバー呼び出しが適用される場合があります。


* **batchLimit**

   連続する呼び出しで送信されるヒット数のしきい値。例えば、この `batchLimit` を 10 に設定した場合は、ヒットが 10 個たまるまでヒットをキューに格納していきます。10 番目のヒットが格納されると、10 個のヒットすべてが連続して送信されます。

   * デフォルト値は `0` です。これはバッチ処理が有効になっていないことを意味します。
   * `offlineEnabled = true` が必要です。
   * 最小 SDK バージョン：4.1

* **charset**

   Analytics に送信されるデータに使用する文字セットを定義します。この文字セットは、受信データを格納およびレポート用に UTF-8 に変換するために使用されます。詳しくは、「[s.charSet](https://marketing.adobe.com/resources/help/ja_JP/sc/implement/charset.html)」を参照してください。

   * 最小 SDK バージョン：4.0

* **clientCode**

   割り当てたクライアントコード。

   >[!IMPORTANT]
   >
   >この変数は Target で必要です。

   * 最小 SDK バージョン：4.0

* **coopUnsafe**

   Device Co-op のユーザーで、この値を `true` に設定する必要がある場合は、Co-op グループに連絡して、お使いの Device Co-op アカウント上でブラックリストフラグをリクエストする必要があります。これらのフラグをセルフサービスで有効にする方法はありません。

   次の情報に留意してください。

   * `coopUnsafe` を `coop_unsafe=1` に設定すると、常に Audience Manager および訪問者 ID ヒットに `true` が追加されます。
   * Audience Manager への Analytics サーバー側の転送を有効にすると、Analytics ヒットに `coop_unsafe=1` も表示されます。
   追加情報を以下に示します。

   * 最小 SDK バージョン：4.16.1
   * `marketingCloud` オブジェクトのブールプロパティが `true` に設定されると、デバイスが Experience Cloud の Device Co-op からオプトアウトします。
   * デフォルト値は `false` です。
   * この設定は、Device Co-op をプロビジョニングしたユーザー&#x200B;**にのみ**&#x200B;適用されます。



* **environmentId**

   使用する環境の ID です。有効な ID（`environmentId=8`）を指定できます。`environmentId` が含まれていない場合、デフォルトの実稼動環境を使用します。

   * 最小 SDK バージョン：4.14

* **lifecycleTimeout**

   デフォルト値は 300 秒です。

   アプリケーションが起動されてから新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

   * 最小 SDK バージョン：4.0

* **messages**

   Adobe Mobile Services によって自動的に生成され、アプリ内メッセージの設定を定義します。詳しくは、以下の「*メッセージの説明*」節を参照してください。

   * 最小 SDK バージョン：4.2

* **offlineEnabled**

   有効にした場合、ヒットはデバイスがオフラインのときにキューに格納され、後でデバイスがオンラインになったときに送信されます。オフライン追跡を使用するには、レポートスイートでタイムスタンプを有効にする必要があります。デフォルト値は `false` です。

   いくつかの重要情報を以下に示します。

   * レポートスイートでタイムスタンプが有効になっている場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* true に設定してください。
   * レポートスイートでタイムスタンプが有効になっていない場合、`offlineEnabled` 設定プロパティを&#x200B;*必ず* false に設定してください。

      このプロパティを適切に設定しなければ、データが失われます。レポートスイートのタイムスタンプが有効になっているかどうか判断できない場合は、カスタマーケアに問い合わせるか、Adobe Mobile Services から設定ファイルをダウンロードしてください。現在、同じレポートスイートで JavaScript と AppMeasurement からデータを収集している場合は、モバイルデータのレポートスイートを個別に設定するか、`s.timestamp` 変数を使用するすべての JavaScript ヒットにカスタムタイムスタンプを含めます。

   * 最小 SDK バージョン：4.0

* **org**

   Adobe Experience Platform ID サービスに Experience Cloud 組織 ID を指定します。

   * 最小 SDK バージョン：4.3

* **poi**

   各 POI 配列は、対象の地点の POI 名、緯度、経度、半径（メートル単位）を保持します。POI 名には任意の文字列を使用できます。`trackLocation` コールの送信時、現在の座標が定義した目標地点内にある場合は、コンテキストデータ変数に代入され、`trackLocation` コールで送信されます。

   * 最小 SDK バージョン：4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >バージョン 4.2 以降、POI は Adobe Mobile インターフェイスで定義され、アプリ設定ファイルに動的に同期されます。この同期をおこなうには、`analytics.poi` 設定が必要です。

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   これを設定しない場合は、`ADBMobile.json` ファイルを更新してこの行を含める必要があります。更新された設定ファイルをダウンロードするには、「[事前設定](/help/ios/getting-started/requirements.md)」を参照してください。

* **postback**

   「コールバック」メッセージテンプレートの定義を次に示します。

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   コード内の `payload` オブジェクトは、`ADBMobileConfig.json` ファイルに追加されるメッセージ定義のサンプルペイロードです。詳しくは、「[ポストバック](/help/ios/analytics-main/postback/postback.md)」を参照してください。

   * 最小 SDK バージョン：4.6

* **privacyDefault**

   * `optedin`：ヒットは即座に送信されます。
   * `optedout`：ヒットは破棄されます。
   * `optunknown`：レポートスイートのタイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      レポートスイートのタイムスタンプが有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      これは初期値を設定するだけです。この値をコードで設定または変更した場合、値が再び変更されるか、アプリがアンインストールされて再インストールされるまで、新しい値が使用されます。デフォルト値は `optedin` です。

   * 最小 SDK バージョン：4.0

* **referrerTimeout**

   SDK が最初の起動時にタイムアウトするまでに獲得リファラーデータを待機する秒数。獲得を使用している場合は、5 秒のタイムアウトをお勧めします。

   >[!IMPORTANT]
   >
   >この変数は獲得で必要です。この変数が `0`、またはこの変数自体が含まれていない場合は、SDK は獲得データを待機せず、獲得指標は追跡されません。

   * 最小 SDK バージョン：4.1

* **remotes**

   自動的に設定され、アドビがホストする、動的設定ファイルのエンドポイントを定義します。起動するたびに各設定ファイルの最終更新時間が現在のバージョンと比較され、更新がダウンロードされて保存されます。

   * `analytics.poi` は、ホストされる POI 設定のエンドポイントです。

   * `messages` は、ホストされるアプリ内メッセージ設定のエンドポイントです。

   * 最小 SDK バージョン：4.2

* **rsids**

   Analytics データを受け取るための 1 つまたは複数のレポートスイート。レポートスイート ID を複数指定する場合は、スペースを入れずにレポートスイート ID をコンマで区切る必要があります。

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >この変数は Analytics で必要です。

   * 最小 SDK バージョン：4.0

* **server**

   親ノードに基づく、Analytics または Audience Management サーバー。

   この変数は、`https://` または `https://` プロトコルプレフィックスを付けずに、サーバードメインを設定する必要があります。プレフィックスは、ライブラリによって自動的に処理され、`ssl` 変数に基づきます。

   `ssl` が `true` の場合、このサーバーとの安全な接続が確立されます。`ssl` が `false` の場合、このサーバーとの安全でない接続が確立されます。

   >[!IMPORTANT]
   >
   >この変数は、Analytics または Audience Management で必要です。

   * 最小 SDK バージョン：4.0

* **ssl**

   >[!IMPORTANT]
   >
   > バージョン 4.10.0 以降では、フラグが設定されていない場合、SSL はデフォルトで true に設定されています。

   SSL（HTTPS）を使用して測定データを送信する機能を有効（`true`）または無効（`false`）にします。

   「コールバック」メッセージテンプレートの定義を次に示します。

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   コードの `payload` オブジェクトは、`ADBMobileConfig.json` ファイルに設定するメッセージ定義のサンプルペイロードです。詳しくは、「[ポストバック](/help/ios/analytics-main/postback/postback.md)」を参照してください。

   * 最小 SDK バージョン：4.0

* **timeout**

   Target が応答を待つ時間を決定します。

   * 最小 SDK バージョン：4.0


## サンプル `ADBMobileConfig.json` ファイル{#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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
         `image` に指定された URL に到達できない場合に使用）
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

* "audiences"

   メッセージの表示方法を定義するオブジェクトの配列です。

   * "key"

      ヒット内で検索する変数名。必須項目です。

   * "matches"

      比較の実行時に使用するマッチャーのタイプ。

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
   * "values"

      次に示す変数の値と一致する値の配列。

      * key
      * と以下に指定されたマッチャ―タイプ
      * matches


* "triggers"

   audiences と同じ。audiences の代わりとなるアクションを次に示します。

   * "key"
   * "matches"
   * "values"
