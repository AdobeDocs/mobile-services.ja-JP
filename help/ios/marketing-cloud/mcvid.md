---
description: Adobe Experience Platform IDサービスは、Experience Cloudソリューション全体でユニバーサル訪問者IDを提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-description: Adobe Experience Platform IDサービスは、Experience Cloudソリューション全体でユニバーサル訪問者IDを提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-title: Experience Cloud ID
solution: Marketing Cloud、Analytics
title: Experience Cloud ID
topic: 開発者と導入
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform IDサービスは、Experience Cloudソリューション全体でユニバーサル訪問者IDを提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。

>[!TIP]
>
>Adobe Experience Platform IDサービスを使用していない限り、Experience Cloud IDに入力する必要はありません。For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**SDK バージョン 4.3 以降が必要**

## Experience Cloud IDの有効化 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. ファイルに `ADBMobileConfig.json` 次の `marketingCloud``org`ファイルが含まれていることを確認します。

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >`@AdobeOrg`含める必要があります。

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 詳しくは [、ADBMobile JSON config](/help/ios/getting-started/requirements.md)を参照してください。

設定後、Experience Cloud ID が生成され、すべてのヒットに含まれます。カスタムや自動生成など、その他の訪問者 ID は、引き続き各ヒットとともに送信されます。
