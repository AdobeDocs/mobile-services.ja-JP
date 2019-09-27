---
description: Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-description: Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-title: Experience Cloud IDの設定
solution: Marketing Cloud,Analytics
title: Experience Cloud ID configuration
topic: 開発者と導入
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Adobe Experience Platform IDサービスは、Experience cloudソリューション全体で汎用の訪問者IDを提供します。 Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。

>[!TIP]
>
>Adobe Experience Platform IDサービスを使用していない場合は、このIDを入力する必要はありません。 For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>この機能には、SDKバージョン4.3以降が必要です。

Experience Cloud ID を有効にするには：

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、 *Core実装およびライフサイクルのIntelliJ IDEAまたはEclipse ProjectへのSDKと設定ファイルの追加*[を参照してください](/help/android/getting-started/dev-qs.md)。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. Verify that the  file contains the :`ADBMobileConfig.json``marketingCloudorg`

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud の組織 ID は、Adobe Experience Cloud 内の各クライアント企業を一意に識別します。次のような値になります。

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >You must include .`@AdobeOrg`

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 詳しくは、[開始する前に](/help/android/getting-started/requirements.md)を参照してください。

設定が完了すると、Experience Cloud ID が生成され、すべてのヒットに含まれます。カスタム ID や自動生成された ID などの他の ID は、引き続きヒットごとに送信されます。
