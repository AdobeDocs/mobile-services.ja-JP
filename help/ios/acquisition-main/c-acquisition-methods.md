---
description: 'iOSライブラリで提供される獲得方法は次のとおりです '
seo-description: 'iOSライブラリで提供される獲得方法は次のとおりです '
seo-title: 獲得メソッド
solution: Marketing Cloud,Analytics
title: 獲得メソッド
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

iOS ライブラリは、以下の獲得メソッドを提供します。

次のメソッドがサポートされています。

* **acquisitionCampaignStartForApp:data:**

   開発者は、ユーザーがダウンロード計測用リンクをクリックしていない場合でも、クリックした場合と同じようにアプリ獲得キャンペーンを開始できます。手動でのダウンロード計測用リンクの作成や、`SKStoreView` と同様に、App Store リダイレクトの処理に役立ちます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


