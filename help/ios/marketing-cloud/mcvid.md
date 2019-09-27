---
description: Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-description: Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: 開発者と導入
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。

>[!TIP]
>
>Adobe Experience Platform IDサービスを使用していない限り、Experience Cloud IDを入力する必要はありません。 For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**SDK バージョン 4.3 以降が必要**

## Experience Cloud IDの有効化 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装とラ *イフサイクルでのプロジェクトへのSDKと設定ファイルの追加* ( [英語のみ)を参照してください](/help/ios/getting-started/dev-qs.md)。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. ファイルに次の内容 `ADBMobileConfig.json` が含まれていることを確認しま `marketingCloud``org`す。

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >を含める必要がありま `@AdobeOrg`す。

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 詳しくは、ADBMobile JSON configを参照 [してください](/help/ios/getting-started/requirements.md)。

設定後、Experience Cloud ID が生成され、すべてのヒットに含まれます。カスタムや自動生成など、その他の訪問者 ID は、引き続き各ヒットとともに送信されます。
