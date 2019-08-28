---
description: デバイス指紋に基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-description: デバイス指紋に基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-title: V3 による獲得のテスト
solution: Marketing Cloud、Analytics
title: V3 による獲得のテスト
uuid: 89137cf-4839-4b37-926e-303cf8e511a5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

デバイス指紋に基づいた V3 による獲得キャンペーンリンクのラウンドトリップに役立つ情報です。

>[!IMPORTANT]
>
>V3獲得は、Adobe Mobile Services UIのダウンロード計測用ビルダーで作成するダウンロード計測用リンクを指します。この機能を使用するには、iOS SDK バージョン 4.6.0 以降にアップグレードする必要があります。

モバイルアプリがまだ App Store にない場合は、キャンペーンリンクの作成時に任意のモバイルアプリをリンク先として選択してください。これは、ダウンロード計測用リンクのクリック後に獲得サーバーによってリダイレクトされるアプリにのみ影響を与えます。リンクのテスト機能には影響を与えません。

1. モバイルアプリ獲得の [前提条件タスクを完了](/help/ios/acquisition-main/acquisition.md)します。
1. Navigate to the **[!UICONTROL Acquisition Builder]** in the Adobe Mobile Services UI and generate an acquisition campaign URL.

   以下に例を示します。

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   ダウンロード計測用リンクで iOS アプリと Android アプリの両方を指す場合は、Apple Store をデフォルトのストアとして使用します。
1. Open the generated link in a desktop browser and go to `https://c00.adobe.com/v3/<appid>/end`.

   JSON 応答の `contextData` は次のようになります。

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. *`appid`* は、ダウンロード計測 *`appid`* 用リンクと同じにする必要があります。 |
   | analytics | `referrerTimeout` は 0 より大きい値です。 |


1. （条件付き）アプリの設定ファイル内の `ssl` 設定が true の場合、HTTPS プロトコルを使用するようにダウンロード計測用リンクを更新します。
1. アプリケーションをインストールするモバイルデバイスから生成されたリンクをクリックします。

   アドビのサーバー（`c00.adobe.com`）がデバイス指紋を保存し、App Store にリダイレクトします。テストのためにアプリをダウンロードする必要はありません。
1. 手順 6 で使用したのと同じモバイルデバイスから、アプリケーションを初めて起動します。

   必要に応じて、アプリを削除してから再度インストールしてください。
1. （オプション）SDK のデバッグログを有効にして、追加の情報を取得することができます。

   すべて正しく機能していれば、ログは次のようになります。

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   ログが上記のようにならない場合は、手順 4 および 5 を実行したことを確認してください。

   以下に、考えられるエラーに関する情報を示します。

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`ネットワークエラーが発生しました。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      応答の形式が正しくありません。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      応答に `contextData` パラメーターがありません。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name``contextData`が含まれていません。

   * `Analytics - Acquisition referrer timed out`

      `referrerTimeout` で定義されている時間内に応答を取得できませんでした。値を増やしてもう一度試してください。ダウンロード計測用リンクを開いてからアプリをインストールすることと、URL のクリック時とアプリの起動時に同じネットワークを使用することも必要です。

      次の情報に留意してください。

      * 獲得サーバーは、リンクのクリック（手順 6）とアプリの起動時（手順 7）に記録された IP アドレスとユーザーエージェント情報に基づいて、アトリビューションを一致させます。

         URL のクリック時とアプリの起動時に同じネットワークを使用する必要があります。

      * HTTP モニタリングツールを使用することによって、アプリから送信されるヒットを監視して、獲得アトリビューションを確認できます。

         `/v3/<appid>/start` 1つのリクエストと、獲得サーバーに送信される `/v3/<appid>/end` リクエストが1つ表示されます。送信されたユーザーエージェントが変わると、アトリビューションが失敗することがあります。

         >[!TIP]
         >
         >ユーザーエージェントの値が `https://c00.adobe.com/v3/<appid>/start` 同じ `https://c00.adobe.com/v3/<appid>/end` であることを確認してください。

      * ダウンロード計測用リンクと SDK からのヒットは、同じ HTTP／HTTPS プロトコルを使用している必要があります。

         異なるプロトコルを使用している（リンクが HTTP を使用し、SDK が HTTPS を使用するなど）場合、（通信事業者によっては）IP アドレスがリクエストごとに異なり、アトリビューションが失敗することがあります。
