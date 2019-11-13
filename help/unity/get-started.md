---
description: このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。
keywords: Unity
seo-description: このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。
seo-title: iOS および Android 4.x SDK 用 Unity プラグイン
solution: Marketing Cloud，開発者
title: iOS および Android 4.x SDK 用 Unity プラグイン
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# iOS および Android 4.x SDK 用 Unity プラグイン {#unity-plug-in-for-the-ios-and-android-x-sdks}

このプラグインを使用すると、Unity プロジェクトから Adobe Analytics コールを送信できます。

Last Updated: **November 12, 2019**

## はじめに {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

GitHub または Developer Connection から [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) ファイルをダウンロードします。

ファイルの内容を次に示し `ADBMobile.unitypackage` ます。

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


オプションのフォルダー：Demo フォルダーには、サポートする各スクリプト言語用の Unity シーンおよびサンプルコードが含まれています。

## ADBMobile プラグインの Unity プロジェクトへの読み込み {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Unity プロジェクトを開きます。
1. Double-click **[!UICONTROL ADBMobile.unitypackage]**.
1. 読み込むフォルダーを選択します。

