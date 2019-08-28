---
title: 開発者クイックスタート
seo-title: BlackBerry Developer Quick Start for Adobe Mobile Services
description: BlackBerry開発者クイックスタートガイドは、Adobe Mobile Services用BlackBerryライブラリの実装プロセスを理解するのに役立ちます。
seo-description: BlackBerry開発者クイックスタートガイドは、Adobe Mobile Services用BlackBerryライブラリの実装プロセスを理解するのに役立ちます。
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# 開発者クイックスタート

この情報は、BlackBerry ライブラリの実装プロセスを理解するために役立ちます。

## SDK の取得

**この SDK を使用するには、BlackBerry 10 以降が必要です。**

ダウンロードした SDK を解凍したら、`AdobeMobile` フォルダーに次のファイルがあることを確認してください。

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## プロジェクトへの SDK の追加

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. **[!UICONTROL 「外部ライブラリ」を選択]** し、「 **[!UICONTROL 次へ]**」をクリックします。
1. 「**[!UICONTROL デバイスライブラリ]」フィールドの横にある「****参照[!UICONTROL 」をクリックします。]**
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動します。
1. `Device-Debug` フォルダー内で、「 `libADBMobileShared.so`**[!UICONTROL 開く]**」を選択します。
1. 「**[!UICONTROL シミュレーターライブラリ]」フィールドの横にある「****参照[!UICONTROL 」をクリックします。]**
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動します。
1. `Device-Debug` フォルダー内で、「 `libADBMobileShared.so`**[!UICONTROL 開く]**」を選択します。
1. 「**[!UICONTROL フォルダーを含める]」フィールドの横にある「****参照[!UICONTROL 」をクリックします。]**
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動します。
1. 含めるフォルダーに `public` フォルダーを追加します。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーには、 `.json` 設定ファイルがあり `ADBMobileConfig.json`ます。

   そのファイルをプロジェクトのルートにコピーします。
1. Right-click on your project and select **[!UICONTROL Refresh]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. プロジェクトの `bar-descriptor.xml` ファイルを開きます。
1. ウィンドウの下部にある「**[!UICONTROL アセット]」タブを選択します。**
1. 「**[!UICONTROL （すべての設定）]**」が選択されていることを確認し、ウィンドウの「**[!UICONTROL アセット]」セクションで「**&#x200B;ファイルを追加&#x200B;**」をクリックします。**
   >[!TIP]
   >
   >QNX ModeFactics IDEには、これらのボタンが表示されないことがあるバグがあります。ボタンが表示されない場合は、表示されるまでウィンドウのサイズを変更してください。

1. **[!UICONTROL 「ワークスペース]**」をクリックします。
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## アプリ権限の追加

`bar-descriptor.xml` プロジェクトディレクトリで、行を追加 `<permission>access_internet</permission>`するか、QNX **[!UICONTROL MobMentics]** IDEで **[!UICONTROL 「アプリケーション]** 」タブの権限セクションの「インターネット」ボックスを選択します。

## `ADBMobileConfig.json` 設定ファイルの更新

`ADBMobileConfig.json` ファイルには、グローバルな SDK 設定が含まれています。最初に、いくつかの値を更新する必要があります。

`ADBMobileConfig.json` ファイルの例を次に示します。

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

You must at least update the `rsids` and `server` parameters. 詳しくは、 [Adobe Mobileクラスおよびメソッドリファレンス](/help/blackberry/methods.md)を参照してください。

これで、BlackBerry 10 アプリに Analytics を実装できるようになりました。
