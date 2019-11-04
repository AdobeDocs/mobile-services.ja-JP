---
description: このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。
seo-title: PhoneGap プラグインの概要
solution: Experience Cloud,Analytics
title: PhoneGap プラグインの概要
topic: 開発者と導入
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# PhoneGap プラグインの概要 {#phonegap-plug-in}

このプラグインを使用すると、PhoneGap プロジェクトから Android AppMeasurement コールを送信できます。PhoneGap プロジェクトを作成するには、[PhoneGap](https://helpx.adobe.com/jp/experience-manager/6-4/mobile/using/phonegap.html) を参照してください。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。


## npm を使用したプラグインのインストール {#section_43229E57C16944C0B51531CB92089189}

次のコマンドを実行します。

```java
cordova plugin add adobe-mobile-services
```

## プラグインの手動インストール{#section_EA1FD59C484D44878AB509954DEE6037}

## プラグインの取り込み

1. `ADBMobile_PhoneGap.java` ファイルを `src` フォルダーにドラッグします。

   このファイルを移動するには、**[!UICONTROL OK]**&#x200B;をクリックします。

1. `ADB_Helper.js` ファイルを、`index.html` ファイルを含むフォルダーにドラッグします。

   このファイルを移動するには、**[!UICONTROL OK]**&#x200B;をクリックします。

1. `res/xml` フォルダーで、`config.xml` を開き、以下の行を追加して新しいプラグインを登録します。

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   例えば、パッケージの名前が `com.example.phonegaptest` の場合、`android-package` の値は次のようになります。

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## AppMeasurement ライブラリの取り込み

1. AppMeasurement ライブラリをダウンロードするには、「[SDK の取得](/help/android/getting-started/dev-qs.md)」を参照してください。
1. `adobeMobileLibrary.jar` ファイルを `src` フォルダーにドラッグします。

   このファイルを移動するには、**[!UICONTROL OK]**&#x200B;をクリックします。

1. 「adobeMobileLibrary.jar」ファイルを右クリックし、**[!UICONTROL ライブラリとして追加]**&#x200B;を参照してください。
1. プロジェクトの要件に基づいて、ライブラリの名前、レベルおよび位置を入力します。
1. `ADBMobileConfig.json` ファイルを、アプリケーションルートの `assets` フォルダーにドラッグします。
1. アプリケーション内のアプリケーション&#x200B;**ではなく**、ルートアプリケーションを選択していることを確認します。

   このファイルを移動するには、**[!UICONTROL OK]**&#x200B;をクリックします。

## アプリの権限の追加

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

## カスタムトラッキングの実装 {#section_FD102B3CDAA4492FB04E56BF17E28663}

`html` ファイル内で、トラッキングを使用する `<head>` タグに次のコードを追加します。

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

