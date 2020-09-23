---
description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
keywords: mobile
seo-description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
seo-title: プッシュメッセージのトラブルシューティング
solution: Experience Cloud,Analytics
title: プッシュメッセージのトラブルシューティング
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 71%

---


# プッシュメッセージのトラブルシューティング{#troubleshooting-push-messaging}

この情報は、プッシュメッセージのトラブルシューティングに役立ちます。

## プッシュメッセージの送信に遅延が生じることがある理由

Mobile Services のプッシュメッセージは、次のタイプの遅延を伴うことがあります。

* **Analytics のヒットの待機**

   どのレポートスイートにも、受信する Analytics のヒットをいつ処理するかを決定する設定があります。デフォルトは 1 時間ごとです。Analytics のヒットの実際の処理にかかる時間は最大 30 分ですが、通常は 15 ～ 20 分です。

   例えば、あるレポートスイートでは 1 時間ごとにヒットが処理されます。処理時間を最大30分に抑えた場合、受信ヒットがプッシュメッセージに使用できるようになるまで、最大90分かかる場合があります。 あるユーザーがアプリを午前 9 時 1 分に起動した場合、ヒットが新しい一意のユーザーとして Mobile Services の UI に表示されるのは、午前 10 時 15 分～ 10 時 30 分になります。

* **プッシュサービスの待機**

   プッシュサービス（APNSまたはGCM）は、メッセージを直ちに送信できない場合があります。 まれではありますが、5 ～ 10 分の遅延が発生したことがあります。メッセージページでは、メッセージの「表示」リンクをクリックして、プッシュメッセージがプッシュサービスに送信されたことを確認できます。レポートでは、成功したプッシュサービスへの送信件数が発行数列に表示されます。

   >[!TIP]
   >
   >プッシュサービスでは、メッセージが送信されることは保証されません。サービスの信頼性について詳しくは、適切なドキュメントを参照してください。
   >
   >* **APNS**: [サービス品質](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [メッセージの有効期間](https://developers.google.com/cloud-messaging/concept-options)


## Appleのプッシュサービス証明書を更新する方法を教えてください。

プッシュメッセージの送信には、有効なプッシュサービス証明書が必要です。 証明書の有効期限が近づいたり、有効期限が切れたりすると、Mobile Services が通知を発行します。この通知を受信したら、以下の手順を実行して、証明書を更新してください。

1. **[!UICONTROL アプリ設定]**&#x200B;をクリックします。
2. 現在の証明書を削除するには、**[!UICONTROL プッシュサービス]**&#x200B;までスクロールして、**[!UICONTROL 削除]**&#x200B;をクリックします。
3. 新しい証明書を設定し、テストします。

   詳しくは、プッシュメッセージを有効にするための [前提条件を参照してください](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. 「**[!UICONTROL 保存]**」をクリックします。

## iOSシミュレーターでプッシュメッセージが表示されないのはなぜですか？

iOSシミュレーターはプッシュメッセージをサポートしていません。
