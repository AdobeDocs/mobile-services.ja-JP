---
description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。
seo-description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。
seo-title: モバイルアプリの獲得
solution: Marketing Cloud,Analytics
title: Mobile app acquisition
topic: 開発者と導入
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。

獲得を使用するには、SDK バージョン 4.1 以降が&#x200B;**必要**&#x200B;です。

ダウンロード計測用リンクは Adobe Mobile Services で作成する必要があります。For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

The information in this section allow the SDK to send acquisition data from an acquisition link.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   > データを複数のレポートスイートに送信する場合は、レポートスイート ID のリスト内の最初のレポートスイートに関連付けられたアプリの獲得設定（獲得サーバーと appid）を使用してください。

   `acquisition` 設定は Adobe Mobile Services によって生成されます。この設定を変更しないでください。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

これらの設定が有効になると、アプリの初回起動後の最初のライフサイクルコールによって獲得データが自動的に送信されます。

>[!CAUTION]
>
>`referrerTimeout`アプリの獲得を有効にするには、 を 0 より大きい値に設定する必要があります。

## ユニバーサルリンク用のiOSアプリの有効化

If you are using Universal Links in your app, add your Adobe Marketing Links domain to the Associated Domains list for your app.

Xcodeで、Adobe Marketing Linksドメインを「関連付けられたドメイン」リストに追加するには：

1. プロジェクトのターゲットに移動し、「機能」タブをク **[!UICONTROL リックし]** ます。
2. 「 **[!UICONTROL Associated Domains]** 」セクションまで下にスクロールし、オンに切り替えます。
3. マーケティングリンクURLから **[!UICONTROL マーケティング]** リンクドメインのドメインリストにエントリを追加します。

入力内容は次のようになりま `applinks:5848561889a02a6996aea62b.c00.adobe.com`す。