---
description: この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
seo-title: バージョン 3 の獲得のテスト
solution: Experience Cloud,Analytics
title: バージョン 3 の獲得のテスト
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 85%

---


# V3 による獲得のテスト {#testing-version-acquisition}

この情報は、Android デバイスでバージョン 3 の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。

>[!IMPORTANT]
>
>V3 での獲得とは、Adobe Mobile Services UI でダウンロード計測ビルダーを使用して作成したダウンロード計測用リンクを指します。この機能を使用するには、Android SDK 4.x forExperience Cloudソリューション4.6.0以降にアップグレードする必要があります。

モバイルアプリがまだGoogle Playにない場合、キャンペーンリンクを作成する際に、目的のモバイルアプリを選択できます。 これは、ダウンロード計測用リンクをクリックした後にダウンロード計測用サーバーがリダイレクトするアプリにのみ影響しますが、リンクのテスト機能には影響しません。クエリ文字列パラメーターは、Google Play ストアに渡され、キャンペーンブロードキャストの一環としてインストール時にアプリに渡されます。ラウンドトリップモバイルアプリの獲得テストでは、このタイプのブロードキャストのシミュレーションが必要です。

>[!IMPORTANT]
>
>Google Play インストールリファラー API を使用して実装する場合、アプリケーションが Google Play ストアに登録される前に獲得のテストをおこなうことはできません。

テストを実行するたびに、アプリを新しくインストールするか、アプリのデータを&#x200B;**[!UICONTROL 設定]**&#x200B;でクリアする必要があります。そうすることで、アプリが最初に起動したときに、キャンペーンクエリ文字列パラメーターに関連付けられている初期ライフサイクル指標が送信されます。

1. 「[モバイルアプリの獲得](/help/android/acquisition-main/acquisition.md)」の前提条件のタスクを実行し、`INSTALL_REFERRER` のブロードキャストレシーバーが正しく実装されていることを確認します。

1. Adobe Mobile Services UI で、**[!UICONTROL 獲得]**／**[!UICONTROL マーケティングリンクビルダー]**&#x200B;をクリックし、Google Play を Android デバイスのリンク先として設定する獲得マーケティングリンク URL を生成します。

   詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。

   例：`https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`。

   >[!TIP]
   >
   >ダウンロード計測用リンクで Android アプリと iOS アプリの両方を参照する場合、Google Play をデフォルトのストアとして使用します。

1. デスクトップのブラウザーで、生成されたリンクを開きます。

   次の例のような URL のページにリダイレクトされます。
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. `utm_content%3D` の後ろにある一意の ID をコピーします。

   前の例では、ID `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3` です。

1. 手順 3 の一意の ID を使用して、次の形式の獲得エンドリンクを作成します。

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`。

   例：`https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`。

1. デスクトップのブラウザーでリンクを開きます。

   JSON 応答に `contextData` が表示されます。

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   `contextData` が表示されない場合、または文字列の一部が表示されない場合、獲得 URL が、[手作業によるダウンロード計測用リンクの作成](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)の形式に従っていることを確認します。
1. 手順 3 を繰り返して、新しい一意の ID を取得します。
1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | サーバー `c00.adobe.com` である必要があります。*`appid`* がダウンロード計測用リンクの `appid` と同じである必要があります。 |
   | analytics | テストの目的で、転送者のタイムアウトを設定し、適切な時間（60 秒以上）を経てブロードキャストが手動で送信されるようにします。テスト後に、元のタイムアウト設定に戻すことができます。 |

1. デバイスをコンピューターに接続し、アプリをアンインストールしてからインストールし直します。
1. ADB Shell を起動し、デバイスでアプリケーションを起動します。
1. 次の `adb` コマンドを使用して、ブロードキャストを送信します。

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. 次の手順を完了します。
   1. `com.adobe.android` をアプリケーションのパッケージ名に置き換えます。
   1. 受信者リファレンスを、アプリ内のキャンペーン追跡受信者の場所の受信者リファレンスに更新します。
   1. `utm_content` に関連付けられた値を置き換えます。

   ブロードキャストが成功すると、次の例のような応答が返されます。

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. （オプション）SDK のデバッグログを有効にして、追加の情報を取得することができます。

   すべて正しく機能していれば、ログは次のようになります。

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

上記のログが表示されない場合は、手順6 ～ 12を実行したことを確認します。

次の表に、考えられるエラーに関する追加情報を示します。

| エラー | 説明 |
|--- |--- |
| Analytics - Unable to decode response(*String*). | 応答の形式が正しくありません。 |
| Analytics - Unable to parse response (*a JSON Response*). | JSON 文字列の形式が正しくありません。 |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | 応答に contextData パラメーターがありません。 |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | contextData に `a.referrer.campaign.name` が含まれていません。 |
| Analytics - Acquisition referrer timed out. | `referrerTimeout` で定義された時間内に応答を取得できませんでした。値を増やしてもう一度試してください。また、アプリをインストールする前に、ダウンロード計測用リンクが開いていることを確認してください。 |

次の情報に留意してください。

* HTTP監視ツールを使用して獲得属性を検証することで、アプリから送信されるヒットを監視できます。
* `INSTALL_REFERRER` のブロードキャスト方法について詳しくは、Google Developers ガイドの [Google Play キャンペーン測定のテスト](https://developers.google.com/analytics/solutions/testing-play-campaigns)を参照してください。

* Android 4.8.2での獲得に関するバグ修正がリリースされました。

   テストを行う前に、SDKを最新バージョンにアップグレードします。

* アドビが提供する `acquisitionTest.jar` Java ツールを使用して、一意の ID を取得し、インストールリファラーをブロードキャストできます。そのため、手順 3 ～ 12 における情報の取得に役立ちます。

   **Javaツールのインストール**

この Java ツールをインストールするには：

1. [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) ファイルをダウンロードします。

1. .jar ファイルを展開します。

   コマンドラインでファイルを実行できます。

   以下に例を示します。

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
