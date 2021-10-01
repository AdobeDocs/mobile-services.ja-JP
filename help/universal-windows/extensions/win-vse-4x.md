---
description: この拡張機能を使用すると、Experience Cloudソリューション 4.x Windows SDK の参照をプロジェクトに追加する際に、はるかに簡単に実行できます。
solution: Experience Cloud,Analytics
title: Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能を使用すると、Experience Cloudソリューション 4.x Windows SDK の参照をプロジェクトに追加する際に、はるかに簡単になります。

## GitHub からのライブラリのインストール {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) から Windows Universal SDK をダウンロードします。
1. ダウンロードしたファイルをローカルに解凍します。
1. **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** ファイルをダブルクリックして、インストーラーを開きます。
1. **[!UICONTROL Global Location]** を選択し、ライブラリをインストールします。

## プロジェクトへの参照の追加 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 プロジェクトを開きます。
1. 「参照マネージャ」(Reference Manager) ダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. 「**[!UICONTROL Adobe]**」タブで、「**[!UICONTROL 拡張機能 Mobile SDK]**」を探して選択します。
1. 「**[!UICONTROL OK]**」をクリックして保存します。

   Adobeモバイル SDK がプロジェクトに追加されます。 **[!UICONTROL Microsoft Visual C++ Runtime]** パッケージがまだ追加されていない場合は、このパッケージもプロジェクトに追加されます。

1. Configuration Manager で、プラットフォームタイプを選択し、アプリのテストを開始します。
