---
description: この拡張機能を使用すると、Experience Cloud ソリューション 4.x Windows SDK の参照を簡単にプロジェクトに追加できるようになります。
seo-description: この拡張機能を使用すると、Experience Cloud ソリューション 4.x Windows SDK の参照を簡単にプロジェクトに追加できるようになります。
seo-title: Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Analytics
title: Experience Cloud Solutions 4.x SDK用Windows Visual studio拡張機能
topic: 開発者と導入
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能を使用すると、Experience Cloud Solutions 4.x Windows SDKの参照をプロジェクトに追加する際に、より簡単に使用できます。

## GitHubからライブラリをインストールする {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) から Windows Universal SDK をダウンロードします。
1. ダウンロードしたファイルをローカルに解凍します。
1. ADBMobileUniversalWindowsVSIX.vsixファイルをダブ **[!UICONTRTOL ルクリックして]** 、インストーラーを開きます。
1. 「グローバ **[!UICONTROL ルな場所」を選択し]** 、ライブラリをインストールします。

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 プロジェクトを開きます。
1. 「参照マネージャ」(Reference Manager)ダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. 「拡張」 **[!UICONTROL タブで]** 、「 **[UICONTROL Adobe Mobile SDK]**」を探して選択します。
1. 「**[!UICONTROL OK]」をクリックして保存します。**

   Adobe Mobile SDKがプロジェクトに追加されます。 UICONTROL **[Microsoft Visual C++ Runtimeパッケージがまだ追加されていない場合]** 、このパッケージもプロジェクトに追加されます。

1. Configuration Managerで、プラットフォームタイプを選択し、アプリのテストを開始します。

