---
description: アプリケーションでプッシュメッセージを設定する前に、いくつかのタスクを完了する必要があります。
keywords: モバイル
seo-description: アプリケーションでプッシュメッセージを設定する前に、いくつかのタスクを完了する必要があります。
seo-title: プッシュメッセージを有効にするための前提条件
solution: Marketing Cloud、Analytics
title: プッシュメッセージを有効にするための前提条件
topic: 指標
uuid: 194e6e07- b794-4152- a838- a4125c3292d4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Prerequisites to enable push messaging {#prerequisites-to-enable-push-messaging}

アプリケーションでプッシュメッセージを設定する前に、これらのタスクを完了する必要があります。

## 貴社のExperience Cloudの有効化

Adobe Analytics を使用する会社では、Experience Cloud を有効にする必要があります。アドビアカウント担当者のステータスを確認できます。

## Mobile SDKのインストールと設定

* **Mobile SDK のインストール**

   プッシュメッセージを設定するには、Mobile SDKのバージョン4.6以降をダウンロードしてインストールする必要があります。For more information, see [Download the SDKs](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **プッシュサービスの設定**

   Mobile SDK でプッシュサービスを設定する必要があります。詳しくは、以下のコンテンツを参照してください。

   * [Androidでのプッシュメッセージ](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [iOSでのプッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)

## Adobe IDを使用してMobileコアサービスにログインします

>[!IMPORTANT]
>
>ユーザーがプッシュサービス機能を使用するには、Adobe IDを使用してMobileコアサービスにログインする必要があります。また、AnalyticsアカウントはAdobe IDにリンクされている必要があります。ユーザーが既存の Adobe Analytics アカウントを使用してログインした場合、プッシュサービス機能は利用できません。

ユーザーが Adobe ID を持っていない場合は、次の手順に従います。

1. (**Experience Cloud Administrator**) Invite users to the Experience Cloud.

1. (**User**) Create a personal Adobe ID using the instructions that you received from the Experience Cloud administrator.

   管理者が前述の手順を完了すると、各ユーザーに対して自動的に電子メールメッセージが送信されます。

1. (**Users**) Log in to Mobile using their Adobe ID.

## Experience Cloudでのユーザーのアカウントのリンク

各ユーザーは、Experience Cloud 組織から Analytics ソリューションアカウントをリンクする必要があります。

1. Adobe ID を使用して Experience Cloud にサインインするには、ブラウザーで「[https://marketing.adobe.com](https://marketing.adobe.com)」と入力します。

1. 右上隅で、Analytics 会社名を選択します。

1. 「**[!UICONTROL 組織を追加]**」をクリックして、ドロップダウンリストから **Adobe SiteCatalyst／Adobe Social[!UICONTROL を選択します。]**

1. Type the company name, your legacy credentials for the specified company, and click **[!UICONTROL Link Account]**.

   これで、Adobe ID が Analytics アカウント、会社およびログイン資格情報にリンクされました。

詳しくは、[アカウントのリンクのトラブルシューティング](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)を参照してください。

## MobileユーザーインターフェイスでのプッシュサービスおよびSDK IDサービスの設定

アプリに対して ID サービスを有効にする前は、「**[!UICONTROL プッシュサービス]」セクションが無効になっています。**&#x200B;ただし、IDサービスを有効にすると、「プッシュサービス」セクションが有効になります。プッシュサービスの有効化について詳しくは、"SDK IDサービスの設定」を参照 [](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)してください。

>[!IMPORTANT]:変更内容を保存してプッシュサービスを更新するには **[!UICONTROL 、「保存」]** をクリックする必要があります。
>
>各レポートスイートでは、Apple 用に 1 つのアプリ、Google 用に 1 つのアプリを設定できます。追加のアプリが必要な場合（例えば、実稼動環境用と開発環境用にアプリが必要な場合）、各間教養に新しいアプリストアアプリと新しいレポートスイートを設定する必要があります。

* **Apple** の場合、秘密鍵および／または証明書をドラッグ＆ドロップします。秘密鍵がパスワードで暗号化されている場合は、パスワードを入力します。

   * **秘密鍵**&#x200B;について、ボックスに秘密鍵ファイルをドラッグ＆ドロップします。

      「**[!UICONTROL 参照]」をクリックしてファイルを選択することもできます。**&#x200B;このファイルには、秘密鍵が含まれています。The certificate might also be included in this file (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * **秘密鍵のパスワード**&#x200B;について、秘密鍵ファイルが暗号化されている場合は、パスワードを入力します。

      （条件付き）**証明書**&#x200B;について、ボックスに証明書ファイルをドラッグ＆ドロップします。「**[!UICONTROL 参照]」をクリックしてファイルを選択することもできます。** This field is not required if the private-key file also contains the certificate ( `.cert`, `.cer`, `.crt`, `.pem`).

* **Google** の場合、アプリの API キーを指定します。

   「**[!UICONTROL テスト]」をクリックして、アプリおよび Mobile Services が正しく設定されていることを確認します。**&#x200B;このオプションは、デバッグおよびトラブルシューティングに役立ちます。

   メッセージを送信するデバイスのプッシュトークンを入力します。複数のトークンをコンマで区切って指定することで、複数のデバイスにメッセージを送信できます。

   ![プッシュテストメッセージ](assets/push_test_list.png)
