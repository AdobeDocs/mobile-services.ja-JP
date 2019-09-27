---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: プロジェクトの構築
solution: Marketing Cloud，開発者
title: プロジェクトの構築
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

iOS 用にビルドする場合、Xcode プロジェクトが作成されます。デフォルトでは、`ADBMobileWrapper.mm` および `AdobeMobileLibrary.a` ファイルが新しいプロジェクトの Libraries グループに存在します。アプリをビルドするために必要な、次の手順を手動で実行します。

1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。

   必要なターゲットのビルドのメンバーであることを確認します。

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(This library might be linked already.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Android 用にビルドする場合、`apk` ファイルの正しい場所に既に `ADBMobileConfig.json` ファイルが含まれています。By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

独自のカスタムマニフェストファイルを使用する必要がある場合、次の変更を加える必要があります。

次の権限を追加します。

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

アプリ内メッセージを使用している場合は、次のアクティビティと受信者を追加します。

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

獲得を使用する場合は、次の受信者を追加します。

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
