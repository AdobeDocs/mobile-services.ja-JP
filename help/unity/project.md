---
description: iOSプロジェクトの構築
keywords: Unity
solution: Experience Cloud Services
title: プロジェクトの構築
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# プロジェクトの構築{#building-your-project}

## iOS

iOS用にをビルドすると、Xcode プロジェクトが作成されます。 デフォルトでは、 `ADBMobileWrapper.mm` および  `AdobeMobileLibrary.a` ファイルは、新しいプロジェクトのライブラリグループに含まれます。 アプリを構築するために必要な、以下の手動の手順を実行します。

1. プロジェクトに `ADBMobileConfig.json` ファイルを追加します。

   必要なターゲットは、ビルドのメンバーであることを確認します。

1. 内 **[!UICONTROL ビルドフェーズ]** プロジェクトの「 」タブで、次のライブラリへのリンクを追加します。

   * `SystemConfiguration.framework`
（このライブラリは既にリンクされている可能性があります。）

   * `libsqlite3.0.dylib`

>[!TIP]
>
>SDK からのローカル通知アプリ内メッセージを使用するには、を呼び出す必要があります `ADBMobile.EnableLocalNotifications();` を、最初の Unity Scene の Start メソッドから削除します。

## Android

Android 向けにをビルドする場合、 `apk` ファイルには既にが含まれています `ADBMobileConfig.json` ファイルを正しい場所に配置する必要があります。 デフォルトでは、 `AndroidManifest.xml` ファイルを `/Plugins/Android` フォルダーも使用されます。

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
