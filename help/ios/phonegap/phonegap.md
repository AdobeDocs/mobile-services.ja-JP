---
description: このプラグインを使用すると、PhoneGap プロジェクトから iOS AppMeasurement コールを送信できます。
keywords: phonegap
seo-description: このプラグインを使用すると、PhoneGap プロジェクトから iOS AppMeasurement コールを送信できます。
seo-title: PhoneGap プラグイン
solution: Marketing Cloud、Analytics
title: PhoneGap プラグイン
topic: 開発者と導入
uuid: f88bcf10-1f9e-4c97- b348-40db797c9923
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap plug-in{#phonegap-plug-in}

このプラグインを使用すると、PhoneGap プロジェクトから iOS AppMeasurement コールを送信できます。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、Launch にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。

PhoneGapプロジェクトを作成するには [、PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html)を参照してください。

## npm を使用したプラグインのインストール: {#section_43229E57C16944C0B51531CB92089189}

1. 次のコマンドを実行します。

   ```
   cordova plugin add adobe-mobile-services
   ```

## プラグインの手動インストール {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### AppMeasurementライブラリのインクルード

AppMeasurement を取り込むには：

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. 以下の設定を実行します。

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. AppMeasurement コードを使用するターゲットを選択します。

1. `ADB_Helper.js` プロジェクト内の `www` フォルダーにドラッグします。
1. `res/xml` フォルダー内で、 `config.xml` 次を追加して新しいプラグインを開き、登録します。

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### アプリ権限の追加

AppMeasurement ライブラリには以下が必要です。

1. Xcode IDE を起動して、アプリを開きます。
1. **[!UICONTROL Adobe Mobile]フォルダーを Xcode プロジェクトにドラッグして、以下の設定を実行します。**

   1. Select **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Select **[!UICONTROL Create groups for any added folders]**.
   1. Select the targets where you want to use AppMeasurement code and click **[!UICONTROL Finish]**.
   ![](assets/xcode-settings.png){width="672"}

1. プロジェクトのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. アプリが予期せぬエラーなくビルドされることを確認します。

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

