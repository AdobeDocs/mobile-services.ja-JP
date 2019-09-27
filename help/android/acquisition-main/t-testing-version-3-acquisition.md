---
description: この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
seo-title: バージョン 3 の獲得のテスト
solution: Marketing Cloud,Analytics
title: バージョン 3 の獲得のテスト
topic: 開発者と導入
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing V3 acquisition {#testing-version-acquisition}

この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。

>[!IMPORTANT]
>
>Acquisition in V3 refers to the acquisition links that you create with the Acquisition Builder in the Adobe Mobile Services UI. この機能を使用するには、Experience Cloud ソリューション 4.6.0 以降用の Android SDK 4.x にアップグレードする必要があります。

モバイルアプリがまだ Google Play に登録されていない場合は、マーケティングリンクを作成するときに任意のモバイルアプリをリンク先として選択できます。これは、ダウンロード計測用リンクのクリック後に獲得サーバーによってリダイレクトされるアプリにのみ影響を与えます。リンクのテスト機能には影響を与えません。クエリ文字列パラメーターは、Google Play ストアに渡されます。これらのパラメーターは、キャンペーンのブロードキャストの一環としてインストール時にアプリに渡されます。モバイルアプリでの獲得のラウンドトリップテストには、このタイプのブロードキャストのシミュレーションが必要です。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. そうすることで、アプリが最初に起動したときに、キャンペーンクエリ文字列パラメーターに関連付けられている初期ライフサイクル指標が送信されます。

1. 「モバイルアプリの獲得」の前提 [条件のタスクを実行し](/help/android/acquisition-main/acquisition.md) 、のブロードキャスト受信機が正しく実装されていることを確認しま `INSTALL_REFERRER`す。
1. In the Adobe Mobile Services UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。

   例：`https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`。

   >[!TIP]
   >
   >If you refer to both Android and iOS apps in the acquisition link, use Google Play as the default store.

1. デスクトップのブラウザーで、生成されたリンクを開きます。

   次の例のような URL のページにリダイレクトされます。
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   前の例では、IDはです `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

1. 手順 3 の一意の ID を使用して、次の形式の獲得エンドリンクを作成します。

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>` で確認します。

   例：`https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

1. デスクトップのブラウザーでリンクを開きます。

   JSON 応答に `contextData` が表示されます。

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   `contextData` が表示されない場合、または文字列の一部が表示されない場合、獲得 URL が、[手作業によるダウンロード計測用リンクの作成](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)の形式に従っていることを確認します。
1. 手順 3 を繰り返して、新しい一意の ID を取得します。
1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | The server should be `c00.adobe.com`.   *`appid`*  should equal the `appid`  in your acquisition link. |
   | analytics | テストのために、ブロードキャストを手動で送信するのに十分な時間（60 秒以上）に送信タイムアウトを設定します。テスト後に元のタイムアウト設定に復元できます。 |

1. デバイスをコンピューターに接続し、アプリをアンインストールしてからインストールし直します。
1. ADB Shell を起動し、デバイスでアプリケーションを起動します。
1. 次の `adb` コマンドを使用して、ブロードキャストを送信します。

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 次の手順を完了します。
   1. `com.adobe.android` をアプリケーションのパッケージ名に置き換えます。
   1. 受信者リファレンスを、アプリ内のキャンペーン追跡受信者の場所の受信者リファレンスに更新します。
   1. Replace values that are associated with `utm_content`.
   ブロードキャストが成功すると、次の例のような応答が返されます。

   `Broadcasting: Intent 
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
Broadcast completed: result=0`

1. （オプション）SDK のデバッグログを有効にして、追加の情報を取得することができます。

   すべてが正しく動作すると、次のようなログが表示されます。

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

これらのログが表示されない場合は、手順 6 ～ 12 が完了していることを確認してください。

次の表には、考えられるエラーに関する追加の情報を示します。

| エラー | 説明 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 応答の形式が正しくありません。 |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 文字列の形式が正しくありません。 |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 応答に contextData パラメーターがありません。 |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  がcontextDataに含まれていない。 |
| Analytics - Acquisition referrer timed out. | `referrerTimeout` で定義された時間内に応答を取得できませんでした。値を増やしてもう一度試してください。また、アプリのインストール前にダウンロード計測用リンクを開いたことも確認してください。 |

次の情報に留意してください。

* アプリから送信されたヒットを監視するには、HTTP 監視ツールを使用して、獲得アトリビューションを確認します。
* `INSTALL_REFERRER` のブロードキャスト方法について詳しくは、Google Developers ガイドの [Google Play キャンペーン測定のテスト](https://developers.google.com/analytics/solutions/testing-play-campaigns)を参照してください。

* Android 4.8.2 での獲得に関して、バグの修正がリリースされました。

   テストをおこなう前に、SDK を最新バージョンにアップグレードしてください。

* アドビが提供する `acquisitionTest.jar` Java ツールを使用して、一意の ID を取得し、インストールリファラーをブロードキャストできます。そのため、手順 3 ～ 12 における情報の取得に役立ちます。

   **Java ツールのインストール**

この Java ツールをインストールするには：

1. Download the [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) file.

1. .jar ファイルを抽出します。

   コマンドラインでファイルを実行できます。

   以下に例を示します。

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
