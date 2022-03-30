---
description: この情報を使用すると、新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。
keywords: モバイル
solution: Experience Cloud Services,Analytics
title: プッシュメッセージの設定
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# プッシュメッセージの設定 {#configure-push-messaging}

この情報を使用すると、新しいアプリの作成中または既存のアプリを編集する際に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。

プッシュメッセージを設定する前に、「[プッシュメッセージを有効にするための前提条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)」の前提条件のタスクを実行します。

* **レポートスイートの考慮事項**

   各レポートスイートでは、Apple 用に 1 つのアプリ、Google 用に 1 つのアプリを設定できます。追加のアプリが必要な場合（例えば、実稼動環境用と開発環境用にアプリが必要な場合）、各環境用に新しいアプリストアアプリと新しいレポートスイートを設定する必要があります。

>[!IMPORTANT]
>
>新しいレポートスイートへのアプリの移行はサポートされていません。新しいレポートスイートに移行すると、プッシュ設定が破損し、メッセージが送信されない可能性があります。

1. 「**[!UICONTROL プッシュサービス]**」で次のフィールドに情報を入力します。

   * Apple

      **[!UICONTROL 秘密鍵]**

      有効な秘密鍵を参照して選択します（`.p12`、`.key`、または `.pen`）。

      >[!IMPORTANT]
      >**[!UICONTROL 秘密鍵]**&#x200B;の入力として選択したファイルに証明書も含まれている場合は、証明書を指定する必要はありません。

   * **[!UICONTROL 証明書]**

      有効な証明書を指定します。このオプションは、**[!UICONTROL 秘密鍵]**&#x200B;の入力に証明書が&#x200B;**含まれていない**&#x200B;場合にのみ必要です。SSL 証明書と秘密鍵の取得について詳しくは、「[APNS または FCM を使用するアプリ設定](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)」を参照してください。

   * Google

      **[!UICONTROL API キー]**

      有効な API キーを指定します。API キーの取得について詳しくは、「[APNS または FCM を使用するアプリ設定](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)」を参照してください。

      詳しくは、次のトピックを参照してください。

      * [Android でのプッシュメッセージ](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOS でのプッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. 「**[!UICONTROL 保存]**」をクリックします。
