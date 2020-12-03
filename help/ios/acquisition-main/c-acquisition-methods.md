---
description: 'iOS ライブラリでは、次の獲得メソッドが提供されています。 '
seo-description: 'iOS ライブラリでは、次の獲得メソッドが提供されています。 '
seo-title: 獲得メソッド
solution: Experience Cloud,Analytics
title: 獲得メソッド
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 100%

---


# 獲得メソッド {#acquisition-methods}

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


