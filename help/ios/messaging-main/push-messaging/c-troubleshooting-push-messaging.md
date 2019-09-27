---
description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
keywords: モバイル
seo-description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
seo-title: プッシュメッセージのトラブルシューティング
solution: Marketing Cloud,Analytics
title: プッシュメッセージのトラブルシューティング
topic: 指標
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Troubleshooting push messaging {#troubleshooting-push-messaging}

この情報は、プッシュメッセージのトラブルシューティングに役立ちます。

## プッシュメッセージの送信に遅延が生じることがある理由

Mobile Services のプッシュメッセージは、次のタイプの遅延を伴うことがあります。

* **Analytics のヒットの待機**

   どのレポートスイートにも、受信する Analytics のヒットをいつ処理するかを決定する設定があります。デフォルトは 1 時間ごとです。Analytics のヒットの実際の処理にかかる時間は最大 30 分ですが、通常は 15 ～ 20 分です。

   例えば、1 時間ごとにヒットを処理するレポートスイートがあるとします。最大 30 分の処理時間を考慮に入れると、プッシュメッセージに対して受信ヒットが利用可能になるまでに最大 90 分かかる場合があります。あるユーザーがアプリを午前 9 時 1 分に起動した場合、ヒットが新しい一意のユーザーとして Mobile Services の UI に表示されるのは、午前 10 時 15 分～ 10 時 30 分になります。

* **プッシュサービスの待機**

   プッシュサービス（APNS または GCM）は、メッセージを直ちに送信できないことがあります。まれではありますが、5 ～ 10 分の遅延が発生したことがあります。メッセージページでは、メッセージの「表示」リンクをクリックして、プッシュメッセージがプッシュサービスに送信されたことを確認できます。レポートでは、成功したプッシュサービスへの送信件数が発行数列に表示されます。

   >[!TIP]
   >
   >プッシュサービスは、メッセージが送信されることを保証しません。 サービスの信頼性について詳しくは、適切なドキュメントを参照してください。
   >
   >* **APNS**：[サービス品質](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**：[メッセージの有効期間](https://developers.google.com/cloud-messaging/concept-options)


## Apple プッシュサービス証明書の更新方法

プッシュメッセージの送信には、有効なプッシュサービス証明書が必要です。証明書の有効期限が近づいたり、有効期限が切れたりすると、Mobile Services が通知を発行します。この通知を受信したら、以下の手順を実行して、証明書を更新してください。

1. Click **[!UICONTROL Manage App Settings]**.
2. To delete the current certificate, scroll to **[!UICONTROL Push Services]** and click **[!UICONTROL Delete]**.
3. 新しい証明書を設定してテストします。

   詳しくは、[プッシュメッセージ有効化の前提条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)を参照してください。

4. 「**[!UICONTROL 保存]**」をクリックします。

## iOS シミュレーターでプッシュメッセージが表示されないのはなぜですか？

iOS シミュレーターは、プッシュメッセージをサポートしません。
