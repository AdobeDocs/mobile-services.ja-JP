---
description: 以下の手順では、Androidデバイス上のマーケティングリンクを使用して獲得キャンペーンをラウンドトリップします。
keywords: android;library;mobile;sdk
seo-description: 以下の手順では、Androidデバイス上のマーケティングリンクを使用して獲得キャンペーンをラウンドトリップします。
seo-title: マーケティングリンクによる獲得のテスト
solution: Marketing Cloud、Analytics
title: マーケティングリンクによる獲得のテスト
topic: 開発者と導入
uuid: d0933dcc-8fc3-4f60-987f-7a54559aaspx5
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

以下の手順では、Androidデバイス上のマーケティングリンクを使用して獲得キャンペーンをラウンドトリップします。

モバイルアプリがまだGoogle Playにない場合は、マーケティングリンクの作成時に任意のモバイルアプリを宛先として選択できます。この設定は、ダウンロード計測用リンクをクリックした後に、獲得サーバーによってどのアプリにリダイレクトされるかに影響するだけで、ダウンロード計測用リンクをテストすること自体には影響しません。クエリ文字列パラメーターは、Google Play ストアに渡されます。これらのパラメーターは、キャンペーンのブロードキャストの一環としてインストール時にアプリに渡されます。モバイルアプリでの獲得のラウンドトリップテストには、このタイプのブロードキャストのシミュレーションが必要です。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. そうすることで、アプリが最初に起動したときに、キャンペーンクエリ文字列パラメーターに関連付けられている初期ライフサイクル指標が送信されます。

1. モバイルアプリの獲得で [前提条件のタスクを完了](/help/android/acquisition-main/acquisition.md) し、ブロードキャスト受信者が正しく実装されていることを確認 `INSTALL_REFERRER`します。
1. In the Adobe Mobile Services] UI, click  **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Links Builder]** and generate an Acquisition Marketing Link URL that sets Google Play as the destination for Android devices.

   詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。

   以下に例を示します。

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 生成されたリンクを Android デバイスで開きます。

   次の例のような URL のページにリダイレクトされます。

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copy the unique ID after `utm_content%3D`.

   前の例では、ID `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`はです。

   デバイスで一意の ID を取得できない場合、デスクトップで次の `CURL` コマンドを実行して、応答文字列から一意の ID を取得します。

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   以下に例を示します。

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. 手順 3 の一意の ID を使用して、次の形式の獲得エンドリンクを作成します。

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   For example, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. ブラウザーでリンクを開きます。

   JSON 応答に `contextData` が表示されます。

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. 手順 3 を繰り返して、新しい一意の ID を取得します。
1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | サーバーは、 `c00.adobe.com`ダウンロード計測 *`appid`* 用リンク `appid` と一致している必要があります。 |
   | analytics | テストのために、ブロードキャストを手動で送信するのに十分な時間（60 秒以上）に送信タイムアウトを設定します。テスト後に元のタイムアウト設定に復元できます。 |

1. デバイスをコンピューターに接続し、アプリをアンインストールしてからインストールし直します。
1. ADB Shell を起動し、デバイスでアプリケーションを起動します。

   ```
   adb shell
   ```

1. 次の `adb` コマンドを使用して、ブロードキャストを送信します。

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. `com.adobe.android` をアプリケーションのパッケージ名に置き換え、受信者リファレンスをアプリ内のキャンペーン追跡受信者の場所のリファレンスに更新します。また、`utm_content` に関連付けられた値を置き換えます。

   ブロードキャストが成功すると、次の例のような応答が返されます。

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. （オプション）SDK のデバッグログを有効にして、追加の情報を取得することができます。

   すべてが正しく動作すると、次のようなログが表示されます。

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   これらのログが表示されない場合は、手順 6 ～ 10 が完了していることを確認してください。

   次の表には、考えられるエラーに関する追加の情報を示します。

   | エラー | 説明 |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | 応答の形式が正しくありません。 |
   | Analytics - Unable to parse response (`a JSON Response`). | JSON 文字列の形式が正しくありません。 |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | 応答に `contextData` パラメーターがありません。 |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` はcontextDataには含まれません。 |
   | Analytics - Acquisition referrer timed out. | `referrerTimeout` で定義された時間内に応答を取得できませんでした。値を増やしてもう一度試してください。また、アプリのインストール前にダウンロード計測用リンクを開いたことも確認してください。 |

次の情報に留意してください。

* アプリから送信されたヒットを監視するには、HTTP 監視ツールを使用して、獲得アトリビューションを確認します。
* `INSTALL_REFERRER` のブロードキャスト方法について詳しくは、Google Developers ガイドの [Google Play キャンペーン測定のテスト](https://developers.google.com/analytics/solutions/testing-play-campaigns)を参照してください。
* アドビが提供する `acquisitionTest.jar` Java ツールを使用して、一意の ID を取得し、インストールリファラーをブロードキャストできます。そのため、手順 3 ～ 10 における情報の取得に役立ちます。

**Javaツールのインストール**

この Java ツールをインストールするには：

1. Download the [`acquistionTester.zip`](../assets/acquisitionTester.zip) file.
1. .jar ファイルを抽出します。

   コマンドラインで .jar ファイルを実行できます。

以下に例を示します。

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

マーケティングリンクは、有効期限が10分のサーバー側でキャッシュされます。マーケティングリストに変更を加えた場合は、リンクを再度使用する前に、変更が適用されるまで約 10 分間待ってください。
