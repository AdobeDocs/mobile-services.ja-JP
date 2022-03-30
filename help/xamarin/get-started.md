---
description: ここでは、Mobile ソリューション 4.x SDK 用 Xamarin コンポーネントの使用を開始する方法について説明します。
keywords: Xamarin
solution: Experience Cloud Services
title: Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネント
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 99%

---

# Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネント {#xamarin-components-for-experience-cloud-solutions-x-sdk}

ここでは、Mobile ソリューション 4.x SDK 用 Xamarin コンポーネントの使用を開始する方法について説明します。

最終更新日：**2019 年 1 月 10 日**

## はじめに {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe モバイル SDK は、Xamarin Components Store や NuGet ギャラリーではご利用いただけません。Xamarin コンポーネントをダウンロードするには、[GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services) に移動します。

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

ADBMobile コンポーネントを Xamarin.Android プロジェクトに読み込みます。

1. Xamarin プロジェクトを開きます。
1. **[!UICONTROL 参照]**&#x200B;ダイアログを開き、「 **[!UICONTROL .ネットアセンブリー]**」タブをクリックします。
1. **[!UICONTROL lib/Android]**&#x200B;フォルダーから `ADBMobile.XamarinAndroidBinding.dll` を選択します。
1. `ADBMobileConfig.json` ファイルをプロジェクトの **[!UICONTROL Assets]** フォルダーに追加します。
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

1. 獲得を使用している場合は、次のレシ―バーを追加します。

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

ADBMobile コンポーネントを Xamarin.iOS プロジェクトに読み込みます。

1. Xamarin プロジェクトを開きます。
1. **[!UICONTROL 参照]**&#x200B;ダイアログを開き、「 **[!UICONTROL .ネットアセンブリー]**」タブをクリックします。
1. **[!UICONTROL lib/ios-unified]** フォルダーから `ADBMobile.XamarinIOSBinding.dll` を選択します。
1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。
