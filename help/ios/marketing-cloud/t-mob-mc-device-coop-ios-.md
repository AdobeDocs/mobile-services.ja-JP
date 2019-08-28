---
description: Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。
seo-description: Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f- ec24-439d-95f0- a246b384b3b5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Experience Cloud Device Co-op の使用を開始するには、アドビの担当者にお問い合わせください。

Experience Cloud Device Co-op に対してモバイルアプリを有効にするには、Experience Cloud iOS SDK の以下の手順を実行します。

>[!IMPORTANT]
>
>この機能には、iOS SDKバージョン4.8.5以降が必要です。

SDK バージョン 4.16.1 以降の Device Co-op ユーザーは、Experience Cloud Device Co-op からモバイルデバイスのデータをオプトアウトできます。詳しくは、[ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)および `visitorAPI.js`isCoopSafe[ 向けの ](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html) メソッドを参照してください。

1. Adobe Mobile SDK を実装します。

   詳しくは、 [コアの実装とライフサイクル](/help/ios/getting-started/dev-qs.md)を参照してください。
1. Experience Cloud ID を有効にします。

   For more information, see [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. ここに記載されているいずれかの同期メソッドを使用して、認証済み ID（CRM ID やハッシュされた電子メールなど）を渡します。

   詳しくは、 [Adobe Experience Platform IDサービスのメソッド](/help/ios/marketing-cloud/mc-methods.md)を参照してください。

## `coopUnsafe` フラグ

`coopUnsafe` フラグについて、次の情報を追加しました。

* 最小 SDK バージョン：4.16.1
* `marketingCloud` オブジェクトのブールプロパティ。このプロパティを設定すると、デバイスがExperience `true`CloudのDevice Co- opをオプトアウトする原因となります。
* Default value is `false`.
* この設定は、Device Co-op をプロビジョニングしたユーザー&#x200B;**にのみ**&#x200B;適用されます。

Device Co-op のユーザーで、この値を `true` に設定する必要がある場合は、Co-op グループに連絡して、お使いの Device Co-op アカウント上でブラックリストフラグをリクエストする必要があります。これらのフラグをセルフサービスで有効にする方法はありません。

次の情報に留意してください。

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Audience Manager への Analytics サーバー側の転送を有効にすると、Analytics ヒットに `coop_unsafe=1` も表示されます。


