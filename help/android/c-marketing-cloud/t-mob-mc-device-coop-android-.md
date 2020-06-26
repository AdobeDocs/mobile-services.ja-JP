---
description: Experience Cloud Device Co-op の使用を開始するには、Adobe 担当者にお問い合わせください。
seo-description: Experience Cloud Device Co-op の使用を開始するには、Adobe 担当者にお問い合わせください。
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: ht
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: ht
source-wordcount: '290'
ht-degree: 100%

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Experience Cloud Device Co-op の使用を開始するには、Adobe 担当者にお問い合わせください。

Experience Cloud Device Co-op 用のモバイルアプリを有効にするには、Experience Cloud Android SDK 用の次の手順を実行します。

>[!IMPORTANT]
>
>この機能には、Android SDK バージョン 4.8.3 以降が必要です。

SDK バージョン 4.16.1 以降、Device Co-op メンバーは、Experience Cloud Device Co-op からモバイルデバイスデータをオプトアウトできます。詳しくは、[ADBMobile JSON 載せ設定](/help/android/configuration/json-config/json-config.md)および [isCoopSafe](https://docs.adobe.com/content/help/ja-JP/id-service/using/id-service-api/configurations/coopsafe.html) 用の `visitorAPI.js` メソッドを参照してください。

1. Adobe Mobile SDK を実装します。

   詳しくは、「[コア実装とライフサイクルい](/help/android/getting-started/dev-qs.md)」を参照してくださ。
1. Experience Cloud ID を有効にします。

   詳しくは、「[Experience Cloud ID の設定](/help/android/c-marketing-cloud/mcvid.md)」を参照してください。
1. いずれかの同期メソッドを使用して、認証済み ID（CRM ID やハッシュされた電子メールなど）を渡します。

   詳しくは、「[Adobe Experience Platform IDサービスのメソッド](/help/android/c-marketing-cloud/mc-methods.md)」を参照してください。

## `coopUnsafe` フラグ

以下に、`coopUnsafe` フラグの追加情報を示します。

* 最小 SDK バージョン：4.16.1
* `marketingCloud` オブジェクトのブールプロパティが `true` に設定されると、デバイスが Experience Cloud の Device Co-op からオプトアウトします。
* デフォルト値は `false` です。
* この設定は、Device Co-op をプロビジョニングしたユーザー&#x200B;**にのみ**&#x200B;適用されます。

Device Co-op のユーザーで、この値を `true` に設定する必要がある場合は、Co-op グループに連絡して、お使いの Device Co-op アカウント上でブロックリストフラグをリクエストする必要があります。これらのフラグをセルフサービスで有効にする方法はありません。

次の情報に留意してください。

* `coopUnsafe` を `coop_unsafe=1` に設定すると、常に Audience Manager および訪問者 ID ヒットに `true` が追加されます。
* Audience Manager への Analytics サーバー側の転送を有効にすると、Analytics ヒットに `coop_unsafe=1` も表示されます。