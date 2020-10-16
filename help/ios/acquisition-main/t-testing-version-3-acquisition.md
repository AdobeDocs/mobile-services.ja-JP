---
description: デバイスのフィンガープリントに基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-description: デバイスのフィンガープリントに基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-title: V3 による獲得のテスト
solution: Experience Cloud,Analytics
title: V3 による獲得のテスト
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '620'
ht-degree: 100%

---


# V3 による獲得のテスト {#testing-v-acquisition}

デバイスのフィンガープリントに基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。

>[!IMPORTANT]
>
>V3 の獲得とは、Adobe Mobile Services UI でダウンロード計測ビルダーを使用して作成した獲得リンクを指します。この機能を使用するには、iOS SDK バージョン 4.6.0 以降にアップグレードする必要があります。

モバイルアプリがまだ App Store にない場合は、キャンペーンリンクを作成する際に、目的のモバイルアプリを選択します。これは、ダウンロード計測用リンクをクリックした後にダウンロード計測用サーバーがリダイレクトするアプリにのみ影響しますが、リンクのテスト機能には影響しません。

1. [モバイルアプリ獲得](/help/ios/acquisition-main/acquisition.md)の前提条件タスクを完了します。
1. Adobe Mobile Services UI で&#x200B;**[!UICONTROL 獲得ビルダー]**&#x200B;に移動し、獲得キャンペーン URL を生成します。

   以下に例を示します。

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   ダウンロード計測用リンクで iOS アプリと Android アプリの両方を参照する場合、Apple Store をデフォルトのストアとして使用します。
1. 生成したリンクをデスクトップブラウザーで開き、`https://c00.adobe.com/v3/<appid>/end` に移動します。

   JSON 応答の `contextData` は次のようになります。

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   `contextData` がない場合や、一部が不足している場合は、獲得 URL が「[手作業によるダウンロード計測用リンクの作成](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)」で指定されている形式に従っていることを確認してください。
1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | サーバー `c00.adobe.com` である必要があります。*`appid`* がダウンロード計測用リンクの *`appid`* と同じである必要があります。 |
   | analytics | `referrerTimeout` は 0 より大きい値です。 |


1. （条件付き）アプリの設定ファイル内の `ssl` 設定が true の場合、HTTPS プロトコルを使用するようにダウンロード計測用リンクを更新します。
1. アプリをインストールする予定のモバイルデバイスから、生成したリンクをクリックします。

   アドビのサーバー（`c00.adobe.com`）がデバイス指紋を保存し、App Store にリダイレクトします。テストのためにアプリをダウンロードする必要はありません。
1. 手順 6 で使用したのと同じモバイルデバイスから、アプリケーションを初めて起動します。

   必要に応じて、アプリを削除してから再度インストールしてください。
1. （オプション）SDK のデバッグログを有効にして、追加の情報を取得することができます。

   すべて正しく機能していれば、ログは次のようになります。

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   上記のログが表示されない場合は、手順 4 と 5 を実行済みであることを確認してください。

   考えられるエラーに関する情報を次に示します。

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`ネットワークエラーが発生しました。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      応答の形式が正しくありません。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      応答に `contextData` パラメーターがありません。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` に `contextData` が含まれていません。

   * `Analytics - Acquisition referrer timed out`

      `referrerTimeout` で定義されている時間内に応答を取得できませんでした。値を増やしてもう一度試してください。また、アプリをインストールする前にダウンロード計測用リンクを開いておき、URL をクリックしてアプリを開いたときにも、同じネットワークを使用していることを確認してください。

      次の情報に留意してください。

      * 獲得サーバーは、リンクのクリック（手順 6）とアプリの起動時（手順 7）に記録された IP アドレスとユーザーエージェント情報に基づいて、アトリビューションを一致させます。

         URL のクリック時とアプリの起動時に同じネットワークを使用する必要があります。

      * HTTP モニタリングツールを使用することによって、アプリから送信されるヒットを監視して、獲得アトリビューションを確認できます。

         `/v3/<appid>/start` リクエスト 1 つと `/v3/<appid>/end` リクエスト 1 つが獲得サーバーに送信されているはずです。送信されたユーザーエージェントが変わると、アトリビューションが失敗することがあります。

         >[!TIP]
         >
         >`https://c00.adobe.com/v3/<appid>/start` と `https://c00.adobe.com/v3/<appid>/end` のユーザーエージェント値が同じなるようにしてください。

      * ダウンロード計測用リンクと SDK からのヒットは、同じ HTTP／HTTPS プロトコルを使用している必要があります。

         異なるプロトコルを使用している（リンクが HTTP を使用し、SDK が HTTPS を使用するなど）場合、（通信事業者によっては）IP アドレスがリクエストごとに異なり、アトリビューションが失敗することがあります。
