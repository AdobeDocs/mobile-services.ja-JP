---
description: この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。
seo-description: この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。
seo-title: Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能
solution: Experience Cloud,Analytics
title: Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---

# Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能を使用すると、Experience Cloudソリューション4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に利用できます。

## GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}からライブラリをインストールします

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)からWindows Universal SDKをダウンロードします。
1. ダウンロードしたファイルをローカルに解凍します。
1. ADBMobileWindowsStoreVSIX.v6またはADBMobileWindowsPhoneVSIX.v6ファイルを重複クリックして、インストーラーを開きます。

1. 「**[!UICONTROL グローバルロケーション]**」を選択し、ライブラリをインストールします。

## プロジ追加ェクト{#section_00C14FE9243D4330BE1F4BB56FCF08B1}への参照

1. Windows 8.1またはWindows Phone 8.1プロジェクトを開きます。
1. 「参照マネージャー」(Reference Manager)ダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. Windows 8.1またはWindows Phone 8.1の&#x200B;**[!UICONTROL エクステンション]**&#x200B;タブで、**[!UICONTROL AdobeモバイルSDK]**&#x200B;を探して選択します。
1. 「**[!UICONTROL OK]**」をクリックして保存します。

   AdobeMobile SDKがプロジェクトに追加されます。まだ追加されていない場合は、**[!UICONTROL Microsoft Visual C++ Runtime]**&#x200B;パッケージも追加されます。

1. Configuration Managerで、プラットフォームタイプを選択し、アプリのテストを開始します。
