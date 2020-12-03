---
description: この情報は、Android デバイスで従来の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android デバイスで従来の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。
seo-title: 従来の獲得のテスト
solution: Experience Cloud,Analytics
title: 従来の獲得のテスト
topic: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 100%

---


# 従来の獲得のテスト {#testing-legacy-acquisition}

この情報は、Android デバイスで従来の獲得キャンペーンリンクをラウンドトリップする場合に役立ちます。

モバイルアプリがまだ Google Play に登録されていない場合は、キャンペーンリンクを作成するときに任意のモバイルアプリをリンク先として選択できます。これは、ダウンロード計測用リンクのクリック後に獲得サーバーによってリダイレクトされるアプリにのみ影響を与えます。ダウンロード計測用リンクのテスト機能には影響を与えません。クエリ文字列パラメーターは、Google Play ストアに渡され、キャンペーンブロードキャストの一環としてインストール時にアプリに渡されます。ラウンドトリップモバイルアプリの獲得テストでは、このタイプのブロードキャストのシミュレーションが必要です。

テストを実行するたびに、アプリを新しくインストールするか、アプリのデータを&#x200B;**[!UICONTROL 設定]**&#x200B;でクリアする必要があります。そうすることで、アプリが最初に起動したときに、キャンペーンクエリ文字列パラメーターに関連付けられている初期ライフサイクル指標が送信されます。

1. Mobile Services UI で、従来の獲得キャンペーン URL を生成します。

   詳しくは、「[従来のダウンロード計測用リンクの使用](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)」を参照してください。
1. デバイスをコンピューターに接続し、ADB Shell を起動して、デバイスでアプリケーションを起動します。
1. 次の形式を使用してブロードキャストを送信します。

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. 次の手順を完了します。
   1. `com.example.adobetesttapp.com` をアプリケーションの逆引き DNS エントリに置き換えます。
   1. 受信者リファレンスを、アプリ内のキャンペーン追跡受信者の場所のリファレンスで更新します。
   1. `utm_source`、`utm_medium`、`utm_term`、`utm_content`、`utm_campaign`などに関連付けられた値を適切な値に置き換えます。

ブロードキャストが成功した場合は、次のような応答が表示されます。

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

また、Adobe のデータ収集サーバーに送信されたイメージリクエストも表示されます。キャンペーンパラメーターを含まないイメージリクエストを使用して、手順 1 で設定したリファラータイムアウトの完了時間が経過すると、SDK はブロードキャストに失敗します。
