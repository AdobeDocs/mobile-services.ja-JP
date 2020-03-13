---
description: このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。
keywords: Unity
seo-description: このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。
seo-title: iOS および Android 4.x SDK 用 Unity プラグイン
solution: Marketing Cloud,Developer
title: iOS および Android 4.x SDK 用 Unity プラグイン
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

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
         * assets

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
