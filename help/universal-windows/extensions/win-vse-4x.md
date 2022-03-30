---
description: この拡張機能を使用すると、Experience Cloudソリューション 4.x Windows SDK の参照をプロジェクトに追加する際に、より簡単に使用できます。
solution: Experience Cloud Services,Analytics
title: Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Experience Cloud ソリューション 4.x SDK 用 Windows Visual Studio 拡張機能 {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

この拡張機能を使用すると、Experience Cloudソリューション 4.x Windows SDK の参照をプロジェクトに追加する際に、はるかに簡単になります。

## GitHub からのライブラリのインストール {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. 次の場所から Windows Universal SDK をダウンロードします。 [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. ダウンロードしたファイルをローカルに解凍します。
1. 次をダブルクリックします。 **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** ファイルを開いてインストーラーを開きます。
1. 選択 **[!UICONTROL グローバルな場所]** ライブラリをインストールします。

## プロジェクトへの参照の追加 {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Windows 10 プロジェクトを開きます。
1. [ 参照マネージャ ] ダイアログボックスを開きます。

   ![](assets/ref_manager.png)

1. の **[!UICONTROL 拡張機能]** タブ、場所、選択 **[!UICONTROL Adobeモバイル SDK]**.
1. クリック **[!UICONTROL OK]** をクリックして保存します。

   AdobeMobile SDK がプロジェクトに追加されます。 この **[!UICONTROL Microsoft Visual C++ Runtime]** パッケージはまだ追加されていません。このパッケージもプロジェクトに追加されます。

1. Configuration Manager で、プラットフォームタイプを選択し、アプリのテストを開始します。
