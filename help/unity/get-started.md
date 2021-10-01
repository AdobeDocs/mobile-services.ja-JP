---
description: このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。
keywords: Unity
solution: Experience Cloud
title: iOS および Android 4.x SDK 用 Unity プラグイン
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
exl-id: fdb012d0-64f5-4c63-96d7-508fef01041f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 100%

---

# iOS および Android 4.x SDK 用 Unity プラグイン {#unity-plug-in-for-the-ios-and-android-x-sdks}

このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。

最終更新日：**2020 年 3 月 10 日**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## はじめに {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

GitHub から ADBMobile.unitypackage ファイルをダウンロードします。

`ADBMobile.unitypackage` ファイルの内容を以下に示します。

* Assets（ルート）

   * ADBMobile

   * プラグイン

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * アセット

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**オプションのフォルダー**：*デモ*&#x200B;フォルダーには、Unity のシーンとサンプルコードが含まれています。

## ADBMobile プラグインの Unity プロジェクトへの読み込み {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Unity プロジェクトを開きます。
1. **[!UICONTROL ADBMobile.unitypackage]** をダブルクリックします。
1. 読み込むフォルダーを選択します。
