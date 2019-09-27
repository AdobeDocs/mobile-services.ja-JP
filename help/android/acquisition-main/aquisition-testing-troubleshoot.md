---
description: The following information helps you troubleshoot Acquisition testing issues.
keywords: android;Acquisition;testing
seo-description: The following information helps you troubleshoot Acquisition testing issues.
seo-title: Troubleshooting Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshooting Acquisition testing
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Troubleshooting Acquisition testing {#aquistion-testing-troubleshooting}

Here are some issues you might face when testing Acquisition and some possible solutions:

* 特に指定しない場合、ADBMobileConfig.jsonファイルはassetsフォルダーに配置する必要があります。

* 名前は大文字と小文字が区別されるので、小文字で名前を付けないでください。

   You need to ensure that  is called from the main activity. `Config.setContext(this.getApplicationContext())`詳しくは、設定方法を参照 [してください](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

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
