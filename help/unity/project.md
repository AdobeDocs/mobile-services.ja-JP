---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: プロジェクトの構築
solution: Experience Cloud
title: プロジェクトの構築
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# プロジェクトの構築{#building-your-project}

## iOS

iOS用にビルドする場合、Xcodeプロジェクトが作成されます。 既定では、 `ADBMobileWrapper.mm` および `AdobeMobileLibrary.a` ファイルは、新しいプロジェクトの[ライブラリ]グループに含まれます。 アプリの作成に必要な次の手順を手動で実行します。

1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。

   必要に応じて、このIDがビルドのメンバーであることを確認します。

1. プロジェクトの「 **[!UICONTROL Build Phases]** （ビルドフェーズ）」タブで、次のライブラリへのリンクを追加します。

   * `SystemConfiguration.framework`
（このライブラリは既にリンクされている可能性があります）。

   * `libsqlite3.0.dylib`

>[!TIP]
>
>SDKからローカル通知のアプリ内メッセージを使用するには、最初のUnityシーンの開始メソッド `ADBMobile.EnableLocalNotifications();` からを呼び出す必要があります。

## Android

Android用にビルドする場合、 `apk` ファイルは既に正しい場所に `ADBMobileConfig.json` ファイルが含まれています。 デフォルトでは、フォルダー内の `AndroidManifest.xml` ファイルも `/Plugins/Android` 使用されます。

独自のカスタムマニフェストファイルを使用する必要がある場合は、次の変更を追加する必要があります。

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
