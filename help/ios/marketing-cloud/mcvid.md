---
description: Adobe Experience Platform ID サービスは、Experience Cloud ソリューション全体に汎用の訪問者 ID を提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 91%

---

# Experience CloudID {#experience-cloud-id}

Adobe Experience Platform ID サービスは、Experience Cloud ソリューション全体に汎用の訪問者 ID を提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。

>[!TIP]
>
>Adobe Experience Platform ID サービスを使用しない場合は、Experience Cloud ID を設定する必要はありません。詳しくは、[Adobe Experience Platform ID サービス ](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=ja) のドキュメントを参照してください。

## Experience Cloud ID の有効化 {#section_79F984271C3B4366B7B04F864F4FF8C2}

これらの手順には、SDK バージョン 4.3 以降が必要です。

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` ファイルに、`marketingCloud` `org` が含まれていることを確認します。

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud 組織 ID は、Adobe Experience Cloud 内の各クライアント企業を一意に識別するもので、`016D5C175213CCA80A490D05@AdobeOrg` のようになります。

   >[!IMPORTANT]
   >
   >`@AdobeOrg` を含める必要があります。

   これらの値が存在しない場合は、Adobe Mobile Services から更新された `ADBMobileConfig.json` ファイルをダウンロードしてください。詳しくは、「[ADBMobile JSON の設定](/help/ios/getting-started/requirements.md)」を参照してください。

設定後、Experience Cloud ID が生成され、すべてのヒットに含まれます。カスタムや自動生成など、その他の訪問者 ID は、引き続き各ヒットとともに送信されます。
