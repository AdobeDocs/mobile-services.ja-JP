---
description: このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。
keywords: android;library;mobile;sdk
seo-description: このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。
seo-title: PhoneGapプラグインの概要
solution: Marketing Cloud、Analytics
title: PhoneGapプラグインの概要
topic: 開発者と導入
uuid: c5c32357- d8df-458a- b0e8- e0c56040241d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGapプラグインの概要 {#phonegap-plug-in}

このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。PhoneGapプロジェクトを作成するには [、PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html)を参照してください。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

>[!IMPORTANT]
>
>2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、[Launch](https://launch.adobe.com/) にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。


## npm を使用したプラグインのインストール {#section_43229E57C16944C0B51531CB92089189}

次のコマンドを実行します。

```java
cordova plugin add adobe-mobile-services
```

## プラグインの手動インストール {#section_EA1FD59C484D44878AB509954DEE6037}

## プラグインの取り込み

1. ファイルを `ADBMobile_PhoneGap.java``src` フォルダーにドラッグします。

   To move this file, click **[!UICONTROL OK]**.

1. ファイルを `ADB_Helper.js` 含むフォルダーにファイルを `index.html` ドラッグします

   To move this file, click **[!UICONTROL OK]**.

1. `res/xml` フォルダー内で `config.xml` 、ファイルを開き、次を追加して新しいプラグインを登録します。

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例えば、パッケージの名前が `com.example.phonegaptest` の場合、`android-package` の値は次のようになります。

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## AppMeasurementライブラリのインクルード

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. `adobeMobileLibrary.jar` ファイルを `src` フォルダーにドラッグします。

   To move this file, click **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. プロジェクトの要件に基づいて、ライブラリの名前、レベルおよび位置を入力します。
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. アプリケーション内のアプリケーション&#x200B;**ではなく**、ルートアプリケーションを選択していることを確認します。

   To move this file, click **[!UICONTROL OK]**.

## アプリ権限の追加

AppMeasurement ライブラリでは、データの送信とオフラインのトラッキングコールの記録のために、次の権限が必要です。

* `INTERNET`
* `ACCESS_NETWORK_STATE`

これらの権限を追加するには、アプリケーションのプロジェクトディレクトリにある `AndroidManifest.xml` ファイルに以下の行を追加します。

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

アプリ内メッセージを有効にするには：

AndroidManifest.xml を更新して、フルスクリーンアクティビティを宣言し、メッセージ通知ハンドラーを有効にします。

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Adobe Mobile Services でメッセージを作成するときにモーダルレイアウトを選択した場合は、次のいずれかのテーマを選択します。

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

以下に例を示します。

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

`html` ファイル内で、トラッキングを使用する `<head>` タグに以下を追加します。

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

