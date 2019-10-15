---
description: 次の情報は、獲得テストの問題のトラブルシューティングに役立ちます。
keywords: android；獲得；テスト
seo-description: 次の情報は、獲得テストの問題のトラブルシューティングに役立ちます。
seo-title: 獲得テストのトラブルシューティング
solution: Marketing Cloud,Analytics
title: 獲得テストのトラブルシューティング
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# 獲得テストのトラブルシューティング {#aquistion-testing-troubleshooting}

獲得をテストする際に直面する可能性のある問題と、考えられる解決策を以下に示します。

* 特に指定しない場合、ADBMobileConfig.jsonファイルはassetsフォルダーに配置する必要があります。

* 名前は大文字と小文字が区別されるので、小文字で名前を付けないでください。

   がメインアクティビティから呼び `Config.setContext(this.getApplicationContext())` 出されていることを確認する必要があります。 詳しくは、設定方法を参照 [してください](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 提供されたAndroidManifest.xmlファイルには、いくつかのユーザー権限がないので、データを送信し、オフライントラッキングコールを記録するために必要です。

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 設定で、リファラータイムアウトがに設定されている場合は、アプリケーションを初めてインストールして起動した後、5秒の時間枠でインストールインテントを送信し、インストールヒットに追加されたリファラー情報を確認する必要があります。 `referrerTimeout: 5`

   手動テストの場合は、インス `referrerTimeout` トールヒットが処理される前にリファラー情報を送信するのに十分な時間があるように、10 ～ 15秒に増やします。

* 「マーケティングリンクの獲得のテスト」のすべ [ての手順を順に実行し](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 、シェルを実行してから `adb` 、次の手順を必ず実行することが重要です。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーインテントを正しく処理するには、これら2つのコマンドを個別に実行する必要があります。  それ以外の場 `adb` 合は、リファラー情報をダブルエスケープし、ブロードキャスト受信機が受信したデータは不完全になります。
