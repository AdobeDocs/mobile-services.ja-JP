---
description: アプリ内およびプッシュメッセージのメッセージレポートを表示できます。
keywords: モバイル
seo-description: アプリ内およびプッシュメッセージのメッセージレポートを表示できます。
seo-title: メッセージレポートの表示
solution: Marketing Cloud、Analytics
title: メッセージレポートの表示
topic: 指標
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

アプリ内およびプッシュメッセージのメッセージレポートを表示できます。

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. **（オプション**）レポートの共通フィルターを作成するか、 **[!UICONTROL カレンダー]** アイコンをクリックして期間を変更します。

   共通フィルターの作成について詳しくは、共通フィルター [の追加を参照](/help/using/usage/reports-customize/t-sticky-filter.md)してください。

>[!TIP]
>
>表示するメッセージの種類によっては、レポートが異なる場合があります。

## In-app messages {#section_90B79BA58E8141F78538C187EB1BF8C7}

アプリ内メッセージに関するレポートを表示する場合、レポートは次の図のようになります。

![レポートメッセージ](assets/report_message.png)

### アプリ内メッセージの指標

アプリ内メッセージで使用できる指標のリストを次に示します。

* **[!UICONTROL メッセージ]**&#x200B;がトリガーされたときのインプレッション。

* **[!UICONTROL クリックスルー]**。ユーザーがアラートまたはフルスクリーンメッセージの **[!UICONTROL 「クリックスルー]** 」ボタンを押すと、ユーザーがローカル通知からアプリを開いたとき。

* **[!UICONTROL キャンセル]**（ユーザーがアラートまたはフルスクリーンメッセージの **[!UICONTROL 「キャンセル」]** ボタンを押すと）

* **[!UICONTROL アクション率]**（Adobe Analyticsの計算指標、クリックスルー数をインプレッション数で割った結果）。

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

プッシュメッセージに関するレポートを表示する場合、レポートは次の図のようになります。

![プッシュメッセージ](assets/report_message_push.png)

上部のグラフには、メッセージを開封したユーザーの数が表示されます。

### プッシュメッセージ指標

プッシュメッセージに使用できる指標のリストを次に示します。

* **[!UICONTROL 時間]**

   メッセージが Mobile Services からデバイスにプッシュされた日時。

* **[!UICONTROL ステータス]**

   メッセージのステータスと使用可能なステータスは次のとおりです。

   * **[!UICONTROL キャンセル]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL 実行中]**
   * **[!UICONTROL 実行済み]**

* **[!UICONTROL 発行数]**

   ユーザーデバイスにメッセージを送信するためにApple Push Notification Service/Firebase Cloud Messaging（APNS/FCM）に正常に送信されたデバイストークンの数。

* **[!UICONTROL 失敗]**

   APNS/FCMに正常に送信されていないデバイストークンの数。失敗の原因となる考えられる理由:

   * 無効な pushID

   * プッシュプラットフォーム（APNS、FCMなど）は、ジョブのアプリケーションには存在しません。（例えば、プラットフォームが iOS プッシュトークンを収集したが、APNS サービスが設定されていない。）

   * メッセージが失敗した原因としては、プッシュサービスが正しく設定されていなかったか、Mobile Services システムがダウンしていることが考えられます。
   >[!IMPORTANT]
   >
   >失敗の数がいつになく多い場合は、プッシュサービスの設定を確認してください。プッシュサービスが正しく設定されていると思われる場合は、アドビカスタマーケアにご連絡ください。

* **[!UICONTROL ブラックリストへの登録]**

   APNSまたはFCMに送信することができないデバイストークンの数。これは、通常、アプリがデバイスからアンインストールされていることや、ユーザーがメッセージを受信するためのオプトイン設定を変更したことを意味します。Android と iOS では、トークンがブラックリストに記載されているものとしてカウントされるタイミングが異なります。Android トークンは、ブラックリストのカウントに即座に表示されます。iOS トークンは、最初は公開されたものとして表示され、APNS からのフィードバックに基づいて、後続のメッセージでブラックリストとして表示されます。
