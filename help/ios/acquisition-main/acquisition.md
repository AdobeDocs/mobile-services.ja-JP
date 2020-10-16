---
description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で AppleApp Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services へと送信します。
seo-description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で AppleApp Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services へと送信します。
seo-title: モバイルアプリの獲得
solution: Experience Cloud,Analytics
title: モバイルアプリの獲得
topic: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '414'
ht-degree: 100%

---


# モバイルアプリの獲得 {#mobile-app-acquisition}

Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で AppleApp Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services へと送信します。

獲得を使用するには、SDK バージョン 4.1 以降が&#x200B;**必要**&#x200B;です。

ダウンロード計測用リンクは、Adobe Mobile Services で作成する必要があります。詳しくは、「[獲得](/help/using/acquisition-main/acquisition-main.md)」を参照してください。

このセクションの情報により、SDK はダウンロード計測用リンクから獲得データを送信できます。

## モバイルアプリの獲得の追跡 {#section_CEA30C652AC8470784B8054E299B80FA}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` ファイルに次の必須の acquisition 設定が含まれていることを確認します。

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

   `acquisition` 設定は Adobe Mobile Services によって生成されます。この設定を変更しないでください。`acquisition` 設定が事前に設定されているカスタマイズ済みの `ADBMobileConfig.json` ファイルをダウンロードする方法について詳しくは、「[事前準備](/help/ios/getting-started/requirements.md)」を参照してください。

これらの設定が有効になると、アプリの初回起動後の最初のライフサイクルコールによって獲得データが自動的に送信されます。

>[!CAUTION]
>
>`referrerTimeout`アプリの獲得を有効にするには、 を 0 より大きい値に設定する必要があります。

## ユニバーサルリンク用の iOS アプリの有効化

アプリでユニバーサルリンクを使用している場合は、アプリの「関連ドメイン」リストにアドビのマーケティングリンクドメインを追加します。

Xcode で、アドビのマーケティングリンクドメインを「関連ドメイン」リストに追加するには、次の手順を実行します。

1. プロジェクトのターゲットに移動し、**[!UICONTROL 機能]**&#x200B;タブをクリックします。
2. 下にスクロールして&#x200B;**[!UICONTROL 関連ドメイン]**&#x200B;セクションに移動し、オンに切り替えます。
3. マーケティングリンク URL から、マーケティングリンクドメインの&#x200B;**[!UICONTROL ドメイン]**&#x200B;リストにエントリを追加します。

入力内容は次のようになります`applinks:5848561889a02a6996aea62b.c00.adobe.com`。