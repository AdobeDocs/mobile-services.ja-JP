---
description: この拡張機能を使用すると、Experience Cloud ソリューション 4.x Windows SDK の参照を簡単にプロジェクトに追加できるようになります。
seo-description: この拡張機能を使用すると、Experience Cloud ソリューション 4.x Windows SDK の参照を簡単にプロジェクトに追加できるようになります。
seo-title: Experience Cloudソリューション4. x SDK用Windows Visual Studio拡張機能
solution: Marketing Cloud、Analytics
title: Experience Cloudソリューション4. x SDK用Windows Visual Studio拡張機能
topic: 開発者と導入
uuid: e48faf54-8b08-4224-9d80- e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能により、プロジェクトにExperience Cloudソリューション4. xのWindows SDKの参照を簡単に追加できます。

## GitHubからのライブラリのインストール {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) から Windows Universal SDK をダウンロードします。
1. ダウンロードしたファイルをローカルに解凍します。
1. **[!UICONTRTOL ADBMobileUniversAllWindowSV6. v6]** ファイルをダブルクリックしてインストーラーを開きます。
1. **[!UICONTROL 「グローバル場所」を選択]** し、ライブラリをインストールします。

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 プロジェクトを開きます。
1. Reference Managerダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. **[!UICONTROL 「エクステンション]** 」タブで、「 **[UACROL Adobe Mobile SDK]**」を検索して選択します。
1. 「**[!UICONTROL OK]」をクリックして保存します。**

   Adobe Mobile SDKがプロジェクトに追加されます。**[UACROL Microsoft Visual C++ランタイム]** パッケージがまだ追加されていない場合、このパッケージもプロジェクトに追加されます。

1. Configuration Managerで、プラットフォームタイプを選択し、アプリのテストを開始します。

