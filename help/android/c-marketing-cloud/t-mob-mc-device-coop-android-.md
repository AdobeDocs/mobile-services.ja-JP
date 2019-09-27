---
description: Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。
seo-description: Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。

Experience Cloud Device Co-op に対してモバイルアプリを有効にするには、Experience Cloud Android SDK の以下の手順を実行します。

>[!IMPORTANT]
>
>This functionality requires Android SDK version 4.8.3 or later.

SDK バージョン 4.16.1 以降の Device Co-op ユーザーは、Experience Cloud Device Co-op からモバイルデバイスのデータをオプトアウトできます。詳しくは、[ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)および `visitorAPI.js`isCoopSafe[ 向けの ](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html) メソッドを参照してください。

1. Adobe Mobile SDK を実装します。

   For more information, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)
1. Experience Cloud ID を有効にします。

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. いずれかの同期メソッドを使用して、認証済み ID（CRM ID やハッシュされた電子メールなど）を渡します。

   詳しくは、 [Adobe Experience Platform IDサービスのメソッドを参照してください](/help/android/c-marketing-cloud/mc-methods.md)。

## `coopUnsafe` フラグ

以下に、`coopUnsafe` フラグの追加情報を示します。

* 最小 SDK バージョン：4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Default value is `false`.
* この設定は、Device Co-op をプロビジョニングしたユーザー&#x200B;**にのみ**&#x200B;適用されます。

Device Co-op のユーザーで、この値を `true` に設定する必要がある場合は、Co-op グループに連絡して、お使いの Device Co-op アカウント上でブラックリストフラグをリクエストする必要があります。これらのフラグをセルフサービスで有効にする方法はありません。

次の情報に留意してください。

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.