---
description: この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。
seo-description: この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。
seo-title: Experience Cloudソリューション4.x SDK用Windows Visual Studio拡張機能
solution: Marketing Cloud,Analytics
title: Experience Cloudソリューション4.x SDK用Windows Visual Studio拡張機能
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: 38e63d6f4f85c2ced6364baa47646241ac783c12
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。

## GitHubからのライブラリのインストール {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. GitHubからWindows Universal SDKをダウンロードし [ます](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)。
1. ダウンロードしたファイルをローカルに解凍します。
1. ADBMobileWindowsStoreVSIX.v6またはADBMobileWindowsPhoneVSIX.v6ファイルを重複クリックして、インストーラーを開きます。

1. 「 **[!UICONTROL グローバルロケーション]** 」を選択し、ライブラリをインストールします。

## プロジ追加ェクトへの参照 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 8.1またはWindows Phone 8.1プロジェクトを開きます。
1. 「参照マネージャー」(Reference Manager)ダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. Windows 8.1またはWindows Phone 8.1の「 **[!UICONTROL Adobe]** 」タブで、「 **[!UICONTROL 拡張機能]**」を探して選択します。
1. Click **[!UICONTROL OK]** to save it.

   AdobeMobile SDKがプロジェクトに追加され、まだ追加されていない場合は、 **[!UICONTROL Microsoft Visual C++ Runtime]** パッケージも追加されます。

1. Configuration Managerで、プラットフォームタイプを選択し、アプリのテストを開始します。

