---
description: iOSプロジェクトの作成
keywords: Unity
solution: Experience Cloud
title: プロジェクトの構築
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# プロジェクトの構築{#building-your-project}

## iOS

iOS用にビルドする場合、Xcodeプロジェクトが作成されます。 デフォルトでは、`ADBMobileWrapper.mm`ファイルと`AdobeMobileLibrary.a`ファイルは、新しいプロジェクトのLibrariesグループに含まれます。 アプリの作成に必要な次の手順を手動で実行します。

1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。

   必要に応じて、このIDがビルドのメンバーであることを確認します。

1. プロジェクトの&#x200B;**[!UICONTROL Build Phases]**&#x200B;タブで、次のライブラリへのリンクを追加します。

   * `SystemConfiguration.framework`
（このライブラリは既にリンクされている可能性があります）。

   * `libsqlite3.0.dylib`

>[!TIP]
>
>SDKからローカル通知のアプリ内メッセージを使用するには、最初のUnityシーンの開始メソッドから`ADBMobile.EnableLocalNotifications();`を呼び出す必要があります。

## Android

Android用にビルドする場合、`apk`ファイルの正しい場所に既に`ADBMobileConfig.json`ファイルが含まれています。 デフォルトでは、`/Plugins/Android`フォルダー内の`AndroidManifest.xml`ファイルも使用されます。

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
