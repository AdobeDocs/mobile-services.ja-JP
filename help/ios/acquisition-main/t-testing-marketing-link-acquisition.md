---
description: デバイスのフィンガープリントに基づくマーケティングリンクを使用した獲得キャンペーンのラウンドトリップに役立つ情報です。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: デバイスのフィンガープリントに基づくマーケティングリンクを使用した獲得キャンペーンのラウンドトリップに役立つ情報です。
seo-title: マーケティングリンクによる獲得のテスト
solution: Experience Cloud,Analytics
title: マーケティングリンクによる獲得のテスト
topic-fix: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
exl-id: 2fb02b36-172e-4c16-9ef9-13f8288ab8a4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 100%

---

# マーケティングリンクによる獲得のテスト {#testing-marketing-link-acquisition}

デバイスのフィンガープリントに基づくマーケティングリンクを使用した獲得キャンペーンのラウンドトリップに役立つ情報です。

1. [モバイルアプリ獲得](/help/ios/acquisition-main/acquisition.md)の前提条件タスクを完了します。
1. Adobe Mobile Services UI で&#x200B;**[!UICONTROL マーケティングリンクビルダー]**&#x200B;をクリックして、App Store を iOS デバイス用のリンク先に設定する獲得マーケティングリンク URL を生成します。

   以下に例を示します。

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。


1. 生成したリンクを iOS デバイスで開き、`https://c00.adobe.com/v3/<appid>/end` を開きます。

   JSON 応答の contextData は次のようになります。

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | サーバー `c00.adobe.com` である必要があります。`appid` がダウンロード計測用リンクの *`appid`* と同じである必要があります。 |
   | analytics | `referrerTimeout` は 0 より大きい値です。 |

1. （条件付き）アプリの設定ファイル内の SSL 設定が `false` の場合、HTTPS の代わりに HTTP プロトコルを使用するようにダウンロード計測用リンクを更新します。
1. アプリをインストールするモバイルデバイスから、生成したリンクをクリックします。

   アドビのサーバー（`c00.adobe.com`）がデバイス指紋を保存し、App Store にリダイレクトします。テストのためにアプリをダウンロードする必要はありません。
1. 手順 6 で使用したのと同じモバイルデバイスから、アプリケーションを初めて起動します。

   必要に応じて、アプリを削除してから再度インストールしてください。
1. （オプション）SDK のデバッグログを有効にして、追加情報を取得します。

   すべて正しく機能していれば、ログは次のようになります。

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   これらのログが表示されない場合は、手順 4 および 5 を実行したことを確認してください。

   考えられるエラーに関する情報を次に示します。

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`：

      ネットワークエラーが発生しました。

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

   `/v3/<appid>/start` リクエスト 1 つと `/v3/<appid>/end` リクエスト 1 つが獲得サーバーに送信されているはずです。

* 送信されたユーザーエージェントが変わると、アトリビューションが失敗することがあります。

   `https://c00.adobe.com/v3/<appid>/start` と `https://c00.adobe.com/v3/<appid>/end` のユーザーエージェント値が同じなるようにしてください。

* ダウンロード計測用リンクと SDK からのヒットは、同じ HTTP／HTTPS プロトコルを使用している必要があります。

   リンクとヒットが異なるプロトコルを使用している（リンクが HTTP を使用し、SDK が HTTPS を使用するなど）場合、通信事業者によっては IP アドレスがリクエストごとに異なることがあります。このため、アトリビューションが失敗する可能性があります。

* マーケティングリンクはサーバー側にキャッシュされ、有効期間は 10 分です。

   マーケティングリンクを変更した場合、リンクを使用するまで約 10 分待つ必要があります。
