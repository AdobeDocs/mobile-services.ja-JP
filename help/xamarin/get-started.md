---
description: ここでは、Mobileソリューション4.x SDK用Xamarinコンポーネントの使用を開始する方法について説明します。
keywords: Xamarin
seo-description: ここでは、Mobileソリューション4.x SDK用Xamarinコンポーネントの使用を開始する方法について説明します。
seo-title: Experience Cloudソリューション4.x SDK用Xamarinコンポーネント
solution: Marketing Cloud,Developer
title: Experience Cloudソリューション4.x SDK用Xamarinコンポーネント
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

ここでは、Mobileソリューション4.x SDK用Xamarinコンポーネントの使用を開始する方法について説明します。

Last Updated: **January 10, 2019**

## はじめに {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>AdobeモバイルSDKは、Xamarin Components StoreやNuGetギャラリーではご利用いただけません。 Xamarinコンポーネントをダウンロードするには、GitHub [に移動します](https://github.com/Adobe-Marketing-Cloud/mobile-services)。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

ADBMobileコンポーネントをXamarin.Androidプロジェクトに読み込みます。

1. Xamarinプロジェクトを開きます。
1. [ **[!UICONTROL 参照]** ]ダイアログを開き、[ **[!UICONTROL .Netアセンブリ]** ]タブをクリックします。
1. `ADBMobile.XamarinAndroidBinding.dll` lib/Android **** フォルダーからを選択します。
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. 次の権限を追加します。

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. アプリ内メッセージを使用している場合は、次のアクティビティと受信者を追加します。

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

ADBMobileコンポーネントをXamarin.iOSプロジェクトに読み込みます。

1. Xamarinプロジェクトを開きます。
1. [ **[!UICONTROL 参照]** ]ダイアログを開き、[ **[!UICONTROL .Netアセンブリ]** ]タブをクリックします。
1. `ADBMobile.XamarinIOSBinding.dll` lib/ios-unified **** フォルダーから選択します。
1. プロジ追加ェクトに `ADBMobileConfig.json` ファイルを追加します。
