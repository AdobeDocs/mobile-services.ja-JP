---
description: アプリ内およびプッシュメッセージのメッセージレポートを表示できます。
keywords: モバイル
seo-description: アプリ内およびプッシュメッセージのメッセージレポートを表示できます。
seo-title: メッセージレポートの表示
solution: Marketing Cloud,Analytics
title: メッセージレポートの表示
topic: 指標
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

アプリ内およびプッシュメッセージのメッセージレポートを表示できます。

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   For more information about creating a sticky filter, see Add a sticky filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)

>[!TIP]
>
>表示しているメッセージのタイプによっては、レポートが異なる場合があります。

## In-app messages {#section_90B79BA58E8141F78538C187EB1BF8C7}

アプリ内メッセージに関するレポートを表示する場合、レポートは次の図のようになります。

![report message](assets/report_message.png)

### In-app message metrics

Here is a list of the metrics that are available for in-app messages:

* **[!UICONTROL インプレッション]**（メッセージがトリガーされたとき）。

* **[!UICONTROL クリックスルー]**、ユーザーが警告メッセージまたはフルスクリーンメッセージの「 **[!UICONTROL Click Through]** 」ボタンを押したとき、およびユーザーがローカル通知からアプリを開いたとき。

* **[!UICONTROL キャンセル]**(ユーザーがアラートまたはフ **[!UICONTROL ルスクリーンメッセージの「キャンセル]** 」ボタンを押したとき)。

* **[!UICONTROL アクション率]**（Adobe Analyticsから計算された指標）は、クリックスルー数をインプレッション数で割った結果です。

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

プッシュメッセージに関するレポートを表示する場合、レポートは次の図のようになります。

![プッシュメッセージ](assets/report_message_push.png)

上部のグラフには、メッセージを開封したユーザーの数が表示されます。

### プッシュメッセージ指標

Here is a list of the metrics that are available for push messages:

* **[!UICONTROL 時間]**

   メッセージが Mobile Services からデバイスにプッシュされた日時。

* **[!UICONTROL ステータス]**

   メッセージのステータスと使用可能なステータスは次のとおりです。

   * **[!UICONTROL Cancelled]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL 実行中]**
   * **[!UICONTROL 実行済み]**

* **[!UICONTROL Published]**

   ユーザーデバイスにメッセージを送信するためにApple Push Notification Service/Firebase Cloud Messaging(APNS/FCM)に正常に送信されたデバイストークンの数です。

* **[!UICONTROL 失敗]**

   The number of device tokens not successfully sent to APNS/FCM. エラーが発生する原因として考えられるものは次のとおりです。

   * 無効な pushID

   * プッシュ先として指定されたプッシュプラットフォーム（APNS、FCMなど）は、ジョブのアプリケーションには存在しません。 （例えば、プラットフォームが iOS プッシュトークンを収集したが、APNS サービスが設定されていない。）

   * メッセージが失敗した原因としては、プッシュサービスが正しく設定されていなかったか、Mobile Services システムがダウンしていることが考えられます。
   >[!IMPORTANT]
   >
   >失敗の数がいつになく多い場合は、プッシュサービスの設定を確認してください。プッシュサービスが正しく設定されていると思われる場合は、アドビカスタマーケアにご連絡ください。

* **[!UICONTROL ブラックリストへの登録]**

   APNSまたはFCMに送信できなくなったデバイストークンの数。 これは、通常、アプリがデバイスからアンインストールされていることや、ユーザーがメッセージを受信するためのオプトイン設定を変更したことを意味します。Android と iOS では、トークンがブラックリストに記載されているものとしてカウントされるタイミングが異なります。Android トークンは、ブラックリストのカウントに即座に表示されます。iOS トークンは、最初は公開されたものとして表示され、APNS からのフィードバックに基づいて、後続のメッセージでブラックリストとして表示されます。
