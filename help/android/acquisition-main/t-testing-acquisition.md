---
description: この情報は、Android デバイスで従来のダウンロード計測キャンペーンリンクをラウンドトリップする場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android デバイスで従来のダウンロード計測キャンペーンリンクをラウンドトリップする場合に役立ちます。
seo-title: 従来のダウンロード計測のテスト
solution: Marketing Cloud,Analytics
title: 従来のダウンロード計測のテスト
topic: 開発者と導入
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

この情報は、Android デバイスで従来のダウンロード計測キャンペーンリンクをラウンドトリップする場合に役立ちます。

モバイルアプリがまだ Google Play に登録されていない場合は、マーケティングリンクを作成するときに任意のモバイルアプリをリンク先として選択できます。この設定は、ダウンロード計測用リンクをクリックした後に、獲得サーバーによってどのアプリにリダイレクトされるかに影響するだけで、ダウンロード計測用リンクをテストすること自体には影響しません。クエリ文字列パラメーターは、Google Play ストアに渡されます。これらのパラメーターは、キャンペーンのブロードキャストの一環としてインストール時にアプリに渡されます。モバイルアプリでの獲得のラウンドトリップテストには、このタイプのブロードキャストのシミュレーションが必要です。

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. そうすることで、アプリが最初に起動したときに、キャンペーンクエリ文字列パラメーターに関連付けられている初期ライフサイクル指標が送信されます。

1. Mobile Services UI で、従来の獲得キャンペーン URL を生成します。

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. デバイスをコンピューターに接続し、ADB Shell を起動して、デバイスでアプリケーションを起動します。
1. 次の形式を使用してブロードキャストを送信します。

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. 次の手順を完了します。
   1. `com.example.adobetesttapp.com` をアプリケーションの逆引き DNS エントリに置き換えます。
   1. 受信者リファレンスを、アプリ内のキャンペーン追跡受信者の場所のリファレンスで更新します。
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

ブロードキャストが成功すると、次のような応答が表示されます。

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

また、アドビのデータ収集サーバーに送信されたイメージリクエストも表示されます。キャンペーンパラメーターが含まれていないイメージリクエストで SDK の待機時間が（手順 1 で設定した）送信タイムアウトの期間を超えた場合、ブロードキャストは失敗です。
