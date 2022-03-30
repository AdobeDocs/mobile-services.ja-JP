---
description: 次の情報は、獲得テストの問題のトラブルシューティングに役立ちます。
keywords: Android; 獲得; テスト
solution: Experience Cloud Services,Analytics
title: 獲得テストのトラブルシューティング
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 100%

---


# 獲得テストのトラブルシューティング {#aquistion-testing-troubleshooting}

獲得をテストする際に直面する可能性のある問題と、考えられる解決策を以下に示します。

* 特に指定しない場合、ADBMobileConfig.json ファイルは assets フォルダーに配置する必要があります。

* 名前では大文字と小文字が区別されるので、名前には小文字を使用しないでください。

   `Config.setContext(this.getApplicationContext())` がメインアクティビティから呼び出されていることを確認する必要があります。詳しくは、「[設定メソッド](../configuration/methods.md)」を参照してください。

* 提供された AndroidManifest.xml ファイルには、データの送信とオフラインのトラッキングコールの記録のために必要な、いくつかのユーザー権限が欠落しています。

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 設定でリファラータイムアウトが `referrerTimeout: 5` に設定されている場合は、アプリケーションを初めてインストールして起動した後、5 秒以内にインストールインテントを送信し、インストールヒットに追加されたリファラー情報を確認する必要があります。

   手動テストの場合は、インストールヒットが処理される前に、リファラー情報を送信するのに十分な時間を確保できるよう、`referrerTimeout` を 10～15 秒に増やします。

* 「[マーケティングリンクの獲得のテスト](t-t-testing-marketing-link-acquisition.md)」のすべての手順を適切な順序で実行し、`adb` シェルを実行してから次の手順を必ず実行することが重要です。

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>リファラーインテントを正しく処理するには、次の 2 つのコマンドを個別に実行する必要があります。そうしないと、`adb` によってリファラー情報がダブルエスケープされ、ブロードキャストレシーバーは不完全なデータを受信することになります。
