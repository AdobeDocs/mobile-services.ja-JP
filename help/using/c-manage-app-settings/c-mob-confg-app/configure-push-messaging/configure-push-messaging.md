---
description: この情報を使用すると、新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。
keywords: モバイル
seo-description: この情報を使用すると、新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページでプッシュサービスオプションを設定するのに役立ちます。
seo-title: プッシュメッセージの設定
solution: Marketing Cloud、Analytics
title: プッシュメッセージの設定
topic: 指標
uuid: 6763858d-6046-4d36-87c0- cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

この情報を使用すると、新規アプリ作成または既存アプリの編集時にアプリ設定ページでプッシュサービスオプションを設定できます。

プッシュメッセージを設定する前に、「プッシュメッセージを有効にするための [前提条件」の前提条件のタスクを実行](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)します。

* **レポートスイートの考慮事項**

   各レポートスイートでは、Apple 用に 1 つのアプリ、Google 用に 1 つのアプリを設定できます。追加のアプリが必要な場合（例えば、実稼動環境用と開発環境用にアプリが必要な場合）、各間教養に新しいアプリストアアプリと新しいレポートスイートを設定する必要があります。

>[!IMPORTANT]
>
>アプリケーションを新しいレポートスイートに移動することはできません。新しいレポートスイートに移行すると、プッシュ設定が破損し、メッセージが送信されない可能性があります。

1. **[!UICONTROL 「プッシュサービス]**」の下の次のフィールドに情報を入力します。

   * Apple

      **[!UICONTROL 秘密鍵]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >**[!UICONTROL 秘密鍵]** の入力用に選択したファイルにも証明書が含まれている場合、証明書を指定する必要はありません。

   * **[!UICONTROL 証明書]**

      有効な証明書を指定します。このオプションは、**[!UICONTROL 秘密鍵]**&#x200B;の入力に証明書が&#x200B;**含まれていない**&#x200B;場合にのみ必要です。SSL証明書および秘密鍵の取得について詳しくは、"APNSまたはFCMを使用するためのアプリケーション [の設定」を参照](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)してください。

   * Google

      **[!UICONTROL API キー]**

      有効な API キーを指定します。APIキーの取得について詳しくは、"APNSまたはFCMを使用するためのアプリ [の設定」を参照](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)してください。

      詳しくは、次のトピックを参照してください。

      * [Androidでのプッシュメッセージ](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [iOSでのプッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. 「**[!UICONTROL 保存]**」をクリックします。
