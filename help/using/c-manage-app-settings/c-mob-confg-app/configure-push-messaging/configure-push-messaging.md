---
description: この情報を使用すると、新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。
keywords: モバイル
seo-description: この情報を使用すると、新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。
seo-title: プッシュメッセージの設定
solution: Marketing Cloud,Analytics
title: プッシュメッセージの設定
topic: 指標
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

この情報を使用して、新しいアプリを作成する場合や既存のアプリを編集する場合に、アプリ設定を管理ページのプッシュサービスオプションを設定できます。

プッシュメッセージを設定する前に、「プッシュメッセージを有効にするための前提 [条件」の前提条件のタスクを実行しま](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)す。

* **レポートスイートの考慮事項**

   各レポートスイートでは、Apple 用に 1 つのアプリ、Google 用に 1 つのアプリを設定できます。追加のアプリが必要な場合（例えば、実稼動環境用と開発環境用にアプリが必要な場合）、各間教養に新しいアプリストアアプリと新しいレポートスイートを設定する必要があります。

>[!IMPORTANT]
>
>Moving your app to a new report suite is not supported. 新しいレポートスイートに移行すると、プッシュ設定が破損し、メッセージが送信されない可能性があります。

1. Type information in the following fields under **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL 秘密鍵]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL 証明書]**

      有効な証明書を指定します。このオプションは、**[!UICONTROL 秘密鍵]**&#x200B;の入力に証明書が&#x200B;**含まれていない**&#x200B;場合にのみ必要です。SSL証明書と秘密鍵の取得について詳しくは、「APNSまたはFCMを使用するた [めのアプリの設定」を参照してください](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

   * Google

      **[!UICONTROL API キー]**

      有効な API キーを指定します。APIキーの取得について詳しくは、APNSまたはFCMを使用する [ようにアプリを設定するを参照してください](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)。

      詳しくは、次のトピックを参照してください。

      * [Androidでのプッシュメッセージ](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOSでのプッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. 「**[!UICONTROL 保存]**」をクリックします。
