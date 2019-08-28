---
description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。
seo-description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。
seo-title: モバイルアプリの獲得
solution: Marketing Cloud、Analytics
title: モバイルアプリの獲得
topic: 開発者と導入
uuid: 5fece619- e4b8-4d06-9250- dcb66fa32ce0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で Apple App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。

獲得を使用するには、SDK バージョン 4.1 以降が&#x200B;**必要**&#x200B;です。

ダウンロード計測用リンクは Adobe Mobile Services で作成する必要があります。For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

この節の情報では、SDKがダウンロード計測用リンクから獲得データを送信できるようにしています。

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
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
   >複数のレポートスイートにデータを送信する場合は、レポートスイートIDのリストにある最初のレポートスイートに関連付けられたアプリから、獲得設定（獲得サーバーとappid）を使用します。

   `acquisition` 設定は Adobe Mobile Services によって生成されます。この設定を変更しないでください。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

これらの設定が有効になると、アプリの初回起動後の最初のライフサイクルコールによって獲得データが自動的に送信されます。

>[!CAUTION]
>
>`referrerTimeout` を0より大きい値に設定して、アプリの獲得を有効にする必要があります。

## ユニバーサルリンク用のiOSアプリの有効化

アプリでユニバーサルリンクを使用している場合は、アプリの「関連ドメイン」リストにAdobe Marketing Linksドメインを追加します。

Xcodeで、Adobe Marketing Linksドメインを関連ドメインリストに追加します。

1. プロジェクトのターゲットに移動し、 **[!UICONTROL 「機能]** 」タブをクリックします。
2. 「関連ドメイン」 **** セクションまで下にスクロールして、オンにします。
3. マーケティングリンクURLからマーケティングリンクドメインの **[!UICONTROL ドメイン]** リストにエントリを追加します。

参加者のエントリ `applinks:5848561889a02a6996aea62b.c00.adobe.com`が表示されます。