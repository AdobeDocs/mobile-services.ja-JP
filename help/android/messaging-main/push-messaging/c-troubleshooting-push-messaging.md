---
description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
keywords: モバイル
seo-description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
seo-title: Troubleshoot Push Messaging
solution: Marketing Cloud,Analytics
title: Troubleshoot Push Messaging
topic: 指標
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Troubleshoot push messaging {#troubleshooting-push-messaging}

この情報は、プッシュメッセージのトラブルシューティングに役立ちます。

## プッシュメッセージの送信に遅延が生じることがある理由

Mobile Services のプッシュメッセージは、次のタイプの遅延を伴うことがあります。

* Analytics のヒットの待機

   どのレポートスイートにも、受信する Analytics のヒットをいつ処理するかを決定する設定があります。デフォルトは 1 時間ごとです。Analytics のヒットの実際の処理にかかる時間は最大 30 分ですが、通常は 15 ～ 20 分です。例えば、1 時間ごとにヒットを処理するレポートスイートがあるとします。最大 30 分の処理時間を考慮に入れると、プッシュメッセージに対して受信ヒットが利用可能になるまでに最大 90 分かかる場合があります。あるユーザーがアプリを午前 9 時 1 分に起動した場合、ヒットが新しい一意のユーザーとして Mobile Services の UI に表示されるのは、午前 10 時 15 分～ 10 時 30 分になります。

* プッシュサービスの待機

   プッシュサービス（APNSまたはFCM）は、メッセージを直ちに送信しない場合があります。 まれではありますが、5 ～ 10 分の遅延が発生したことがあります。メッセージページでは、メッセージの「**表示**」リンクをクリックして、プッシュメッセージがプッシュサービスに送信されたことを確認できます。レポートでは、成功したプッシュサービスへの送信件数が&#x200B;**[!UICONTROL 発行数]列に表示されます。**

   >[!TIP]
   >
   >プッシュサービスは、メッセージが送信されることを保証しません。

   サービスの信頼性について詳しくは、適切なドキュメントを参照してください。

   * **APNS**：[サービス品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**:メッ [セージの有効期間](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## プッシュメッセージが途中で切れたり、展開されなかったりする理由

Android デバイスによっては、メッセージを表示するときに、`NotificationCompat.BigTextStyle` を使用しなければならない場合があります。
