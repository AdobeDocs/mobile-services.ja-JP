---
description: 以下の情報は、獲得テストの問題のトラブルシューティングに役立ちます。
keywords: android;獲得、テスト
seo-description: 以下の情報は、獲得テストの問題のトラブルシューティングに役立ちます。
seo-title: 獲得テストのトラブルシューティング
solution: Marketing Cloud、Analytics
title: 獲得テストのトラブルシューティング
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# 獲得テストのトラブルシューティング {#aquistion-testing-troubleshooting}

獲得テスト時に直面する可能性のある問題と、いくつかの解決策を以下に示します。

* それ以外の場合は、ADBMobileConfig. jsonファイルをassetsフォルダーに配置します。

* 名前では大文字と小文字が区別されるので、小文字の文字には名前を指定しないでください。

   メインアクティビティから `Config.setContext(this.getApplicationContext())` 呼び出されることを確認する必要があります。詳しくは [、設定メソッド](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)を参照してください。

* 提供されたAndroidManifest.xmlファイルにいくつかのユーザー権限がありません。これらの権限は、データを送信し、オフライントラッキングコールを記録するために必要です。

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 設定では、リファラータイムアウトが設定されている場合 `referrerTimeout: 5`、アプリケーションがインストールされ、初回起動された時点で5秒の時間枠にインストールインテントを送信する必要があり、インストールヒットに追加されたリファラー情報を確認する必要があります。

   手動テストの場合、インストール `referrerTimeout` ヒットの処理前にリファラー情報を送信するのに十分な時間があることを、10~15秒に増やします。

* マーケティングリンクの獲得 [](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) のテストのすべての手順を実行して、シェルを実行し、 `adb` 次の手順を実行することが重要です。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーインテントを正しく処理するには、これら2つのコマンドを個別に実行する必要があります。そうしないと、リファラー情報が `adb` 二重にエスケープされ、ブロードキャスト受信者によって受信されたデータは不完全になります。
