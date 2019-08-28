---
description: ここでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
keywords: android;library;mobile;sdk
seo-description: ここでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。
seo-title: 獲得テストのトラブルシューティング
solution: Marketing Cloud、Analytics
title: 獲得テストのトラブルシューティング
topic: 開発者と導入
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 獲得テストのトラブルシューティング {#troubleshoot-acquisition-testing}

ここでは、獲得テスト中に直面する可能性のある問題のトラブルシューティング方法について説明します。

* それ以外の場合は、ADBMobileConfig. jsonファイルを `assets` フォルダー内に配置する必要があります。

   名前では大文字と小文字が区別されるので、大文字または小文字の文字を使用しないでください。

* メインアクティビティ `Config.setContext(this.getApplicationContext())` から呼び出されることを確認します。

   詳しくは [、設定メソッド](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)を参照してください。

* Mobile SDKに必要な権限が `AndroidManifest.xml` ファイル内にあることを確認します。

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* `referrerTimeout` AdMobileConfig. jsonファイルの5に設定されている場合、アプリケーションがインストールされ、初回起動された後、インストールヒットに追加されたリファラー情報を確認するために、インストールインテントを5秒の時間枠で送信する必要があります。

   手動テストでは、インストールヒットの処理 `referrerTimeout` 前にリファラー情報を送信するのに十分な時間があることを、10~15秒に増やすことをお勧めします。

* 「マーケティングリンクのテスト [」のすべての手順を実行](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) し、最初にコマンドを `adb shell` 実行して次の手順を実行します。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーインテントを正しく処理するには、これら2つのコマンドを個別に実行する必要があります。そう `adb` しないと、リファラー情報が二重にエスケープされ、ブロードキャスト受信者によって受信されたデータは不完全になります。

