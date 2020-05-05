---
description: Adobe Experience Platform ID サービスは、Experience Cloud ソリューション全体に汎用の訪問者 ID を提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-description: Adobe Experience Platform ID サービスは、Experience Cloud ソリューション全体に汎用の訪問者 ID を提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。
seo-title: Experience Cloud ID の設定
solution: Marketing Cloud,Analytics
title: Experience Cloud ID の設定
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud ID の設定 {#experience-cloud-id-configuration}

Adobe Experience Platform ID サービスは、Experience Cloud ソリューション全体に汎用の訪問者 ID を提供します。Analytics は、Target、ビデオのハートビート、将来の Experience Cloud 統合に ID サービスを必要とします。

>[!TIP]
>
>Adobe Experience Platform ID サービスを使用しない場合は、この ID を設定する必要はありません。詳しくは、「[Adobe Experience Platform ID サービス](https://docs.adobe.com/content/help/ja-JP/id-service/using/home.html)」を参照してください。

>[!IMPORTANT]
>
>この機能には、SDK バージョン 4.3 以降が必要です。

Experience Cloud ID を有効にするには：

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. `ADBMobileConfig.json` ファイルに `marketingCloudorg` が含まれていることを確認します。

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
   >`@AdobeOrg` を含める必要があります。

   これらの ID が設定されていない場合は、更新された `ADBMobileConfig.json` ファイルを Adobe Mobile Services からダウンロードしてください。詳しくは、[事前準備](/help/android/getting-started/requirements.md)を参照してください。

設定が完了すると、Experience Cloud IDが生成され、すべてのヒットに含められます。 その他のID（カスタムIDや自動生成IDなど）は、各ヒットで引き続き送信されます。
