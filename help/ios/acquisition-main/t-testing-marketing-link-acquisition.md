---
description: 以下の手順は、デバイスの指紋に基づくマーケティングリンクを使用して、獲得キャンペーンをラウンドトリップする場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: 以下の手順は、デバイスの指紋に基づくマーケティングリンクを使用して、獲得キャンペーンをラウンドトリップする場合に役立ちます。
seo-title: マーケティングリンク獲得のテスト
solution: Marketing Cloud,Analytics
title: マーケティングリンク獲得のテスト
topic: 開発者と導入
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

The following instructions help you roundtrip an acquisition campaign with a Marketing Link that is based on a device fingerprint.

1. [モバイルアプリ獲得](/help/ios/acquisition-main/acquisition.md)の前提条件タスクを完了します。
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   以下に例を示します。

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   JSON 応答の contextData は次のようになります。

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. 設定ファイルの次の設定が正しいことを確認します。

   | 設定 | 値 |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` should equal the  *`appid`* in your acquisition link. |
   | analytics | `referrerTimeout` は 0 より大きい値です。 |

1. （条件付き）アプリの設定ファイル内の SSL 設定が `false` の場合、HTTPS の代わりに HTTP プロトコルを使用するようにダウンロード計測用リンクを更新します。
1. アプリをインストールするモバイルデバイスから、生成したリンクをクリックします。

   アドビのサーバー（`c00.adobe.com`）がデバイス指紋を保存し、App Store にリダイレクトします。テストのためにアプリをダウンロードする必要はありません。
1. 手順 6 で使用したのと同じモバイルデバイスから、アプリケーションを初めて起動します。

   必要に応じて、アプリを削除してから再度インストールしてください。
1. （オプション）SDK のデバッグログを有効にして、追加情報を取得します。

   すべてが正しく動作すると、次のようなログが表示されます。

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   これらのログが表示されない場合は、手順4と5が完了していることを確認します。

   考えられるエラーに関する情報を次に示します。

   *  を使用します`Analytics - Unable to retrieve acquisition service response (<error message>)`。

      ネットワークエラーが発生しました。

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      応答の形式が正しくありません。

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      応答に `contextData` パラメーターがありません。

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` is not included in `contextData`.

   * `Analytics - Acquisition referrer timed out`

      `referrerTimeout` で定義されている時間内に応答を取得できませんでした。値を増やしてもう一度試してください。ダウンロード計測用リンクを開いてからアプリをインストールすることと、URL のクリック時とアプリの起動時に同じネットワークを使用することも必要です。

次の情報に留意してください。

* 獲得サーバーは、リンクのクリック（手順 6）とアプリの起動時（手順 7）に記録された IP アドレスとユーザーエージェント情報に基づいて、アトリビューションを一致させます。

   URL のクリック時とアプリの起動時に同じネットワークを使用する必要があります。

* HTTP モニタリングツールを使用することによって、アプリから送信されるヒットを監視して、獲得アトリビューションを確認できます。

   `/v3/<appid>/start` リクエスト 1 つと `/v3/<appid>/end` リクエスト 1 つが獲得サーバーに送信されているはずです。

* 送信されたユーザーエージェントが変わると、アトリビューションが失敗することがあります。

   Ensure that  and  have the same user-agent values.`https://c00.adobe.com/v3/<appid>/start``https://c00.adobe.com/v3/<appid>/end`

* ダウンロード計測用リンクと SDK からのヒットは、同じ HTTP／HTTPS プロトコルを使用している必要があります。

   リンクとヒットが異なるプロトコルを使用している場合（例えば、リンクがHTTPを使用し、SDKがHTTPSを使用する場合）、IPアドレスはリクエストごとに通信事業者によって異なる場合があります。 このため、アトリビューションが失敗する可能性があります。

* マーケティングリンクは、10分の有効期限が設定されたサーバー側でキャッシュされます。

   マーケティングリンクに変更を加える場合は、リンクを使用する前に約10分待つ必要があります。