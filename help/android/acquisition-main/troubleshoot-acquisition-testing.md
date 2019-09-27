---
description: このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
keywords: android;library;mobile;sdk
seo-description: このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
seo-title: 獲得テストのトラブルシューティング
solution: Marketing Cloud,Analytics
title: 獲得テストのトラブルシューティング
topic: 開発者と導入
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 獲得テストのトラブルシューティング {#troubleshoot-acquisition-testing}

このトピックでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。

* 特に指定しない場合は、ADBMobileConfig.jsonファイルをフォルダーに配置する必要があり `assets` ます。

   名前では大文字と小文字が区別されるので、大文字と小文字を区別しないでください。

* がメインアクティビティ `Config.setContext(this.getApplicationContext())` から呼び出されていることを確認します。

   詳しくは、設定方法を参照 [してください](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* Mobile SDKに必要な権限がファイル内に存在することを確認し `AndroidManifest.xml` ます。

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* ADMobileConfig.jsonファイル `referrerTimeout` でが5に設定されている場合、インストールヒットに追加されたリファラー情報を確認するには、アプリケーションを初めてインストールして起動した後、5秒の時間枠でインストールインテントを送信する必要があります。

   手動テストの場合は、インストールヒットが処理される前にリファラー情報を送信するのに十分な時間を確保できるように、 `referrerTimeout` 10 ～ 15秒に増やすことをお勧めします。

* 「マーケティングリンク獲得のテ [スト](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 」のすべての手順を実行し、最初にコマンドを実行し `adb shell` 、次の手順を必ず実行してください。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーの意図を正しく処理するには、これら2つのコマンドを個別に実行する必要があります。 そうしな `adb` いと、リファラー情報が二重にエスケープされ、ブロードキャスト受信機が受信したデータは不完全になります。

