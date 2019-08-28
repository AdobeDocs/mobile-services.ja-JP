---
description: ここでは、Mobile ソリューション 4.x SDK 用 Xamarin コンポーネントを使い始める方法を説明します。
keywords: Xamarin
seo-description: ここでは、Mobile ソリューション 4.x SDK 用 Xamarin コンポーネントを使い始める方法を説明します。
seo-title: Experience Cloudソリューション4. x SDK用Xamarinコンポーネント
solution: Marketing Cloud，開発者
title: Experience Cloudソリューション4. x SDK用Xamarinコンポーネント
uuid: e7a48107- bd0e-47d6- b49c- dfcae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

ここでは、Mobile ソリューション 4.x SDK 用 Xamarin コンポーネントを使い始める方法を説明します。

最終更新日：**2019 年 1 月 10 日**

## 導入 {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDKは、XamarinコンポーネントストアまたはnumGetギャラリーでは使用できなくなりました。Xamarin コンポーネントにダウンロードするには、[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services) にアクセスしてください。


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

ADBMobileコンポーネントをXamarin. Androidプロジェクトに読み込みます。

1. Xamarinプロジェクトを開きます

1. **[!UICONTROL References]** ダイアログを開き、 **[!UICONTROL ". Net Assembly]** 」タブをクリックします。

1. `ADBMobile.XamarinAndroidBinding.dll`**[!UICONTROL lib/Android]** フォルダーから選択します。

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. 次の権限を追加します。

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. アプリ内メッセージを使用している場合は、次のアクティビティおよび受信者を追加します。

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. 獲得を使用している場合は、次の受信者を追加します。

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

ADBMobileコンポーネントをXamarin. iOSプロジェクトに読み込みます。

1. Xamarinプロジェクトを開きます。
1. **[!UICONTROL References]** ダイアログを開き、 **[!UICONTROL ". Net Assembly]** 」タブをクリックします。

1. `ADBMobile.XamarinIOSBinding.dll`**[!UICONTROL lib/ios- unified]** フォルダーから選択します。

1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。


