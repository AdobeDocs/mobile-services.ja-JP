---
description: このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
keywords: android;library;mobile;sdk
seo-description: このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
seo-title: 獲得テストのトラブルシューティング
solution: Experience Cloud,Analytics
title: 獲得テストのトラブルシューティング
topic: Developer and implementation
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 100%

---


# 獲得テストのトラブルシューティング {#troubleshoot-acquisition-testing}

このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。

* 特に指定しない場合、ADBMobileConfig.json ファイルは `assets` フォルダーに配置する必要があります。

   名前では大文字と小文字が区別されるので、名前には大文字と小文字を混在させて使用しないでください。

* `Config.setContext(this.getApplicationContext())` がメインアクティビティから呼び出されていることを確認します。

   詳しくは、「[設定メソッド](https://docs.adobe.com/content/help/ja-JP/mobile-services/android/configuration-android/methods.html)」を参照してください。

* Mobile SDK に必要な権限が `AndroidManifest.xml` ファイル内に存在することを確認します。

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* ADMobileConfig.json ファイルで `referrerTimeout` でが 5 に設定されている場合、アプリケーションを初めてインストールして起動した後、5 秒以内にインストールインテントを送信し、インストールヒットに追加されたリファラー情報を確認する必要があります。

   手動テストの場合は、インストールヒットが処理される前に、リファラー情報を送信するのに十分な時間を確保できるよう、`referrerTimeout` を 10～15 秒に増やすことをお勧めします。

* 「[マーケティングリンク獲得のテスト](https://docs.adobe.com/content/help/ja-JP/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)」のすべての手順を実行し、必ず最初に `adb shell` コマンドを実行してから次の手順を実行するようにしてください。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーインテントを正しく処理するには、次の 2 つのコマンドを個別に実行する必要があります。`adb`そうしないと、リファラー情報がダブルエスケープされ、ブロードキャストレシーバーは不完全なデータを受信することになります。

