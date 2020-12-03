---
title: 開発者クイック開始
seo-title: AdobeMobile Services用BlackBerry開発者クイック開始
description: 『BlackBerry開発者クイック開始ガイド』は、AdobeMobile Services用のBlackBerryライブラリを実装するプロセスを理解するのに役立ちます。
seo-description: 『BlackBerry開発者クイック開始ガイド』は、AdobeMobile Services用のBlackBerryライブラリを実装するプロセスを理解するのに役立ちます。
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 5%

---


# 開発者向けクイックスタート

この情報は、BlackBerryライブラリを実装するプロセスを理解するうえで役立ちます。

## SDK の取得

**SDKにはBlackBerry 10以降が必要です。**

ダウンロードしたSDKを解凍した後、次のファイルがフォルダーに存在することを確認し `AdobeMobile` ます。

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

## プロジ追加ェクトへのSDK

1. プロジェクトを右クリックし、 **[!UICONTROL 設定]** / **[!UICONTROL 追加ライブラリを選択します]**。
1. 「 **[!UICONTROL 外部ライブラリ]** 」を選択し、「 **[!UICONTROL 次へ]**」をクリックします。
1. 「 **[!UICONTROL デバイスライブラリ]** 」フィールドの横にある「参照 **** 」をクリックします。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. フォルダーでを選択し、「 `Device-Debug` 開く `libADBMobileShared.so`****」をクリックします。
1. 「 **[!UICONTROL シミュレーターライブラリ]** 」フィールドの横にある「参照 **** 」をクリックします。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. フォルダーでを選択し、「 `Device-Debug` 開く `libADBMobileShared.so`****」をクリックします。
1. 「フォルダを **[!UICONTROL 含める]** 」 **[!UICONTROL フィールドの横にあるをクリックします]** 。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. 含め追加る `public` フォルダー。
1. この `ADBMobile-4.0.0BETA-BlackBerry` フォルダーには、という名前の `.json` 設定ファイルがあり `ADBMobileConfig.json`ます。

   そのファイルをプロジェクトのルートにコピーします。
1. プロジェクトを右クリックし、「 **[!UICONTROL 更新]**」を選択します。

   これで、 `.json` ファイルが **[!UICONTROL プロジェクトエクスプローラに表示されます]**。
1. プロジェクトの `bar-descriptor.xml` ファイルを開きます。
1. ウィンドウの下部で、「 **[!UICONTROL アセット]** 」タブを選択します。
1. 「 **[!UICONTROL (All Configurations)]** 」が選択されていることを確認し、ウィンドウの「 **[!UICONTROL Assets]** 」セクションで「ファイル **** 」をクリックします。
   >[!TIP]
   >
   >QNX Momentics IDEには、ボタンが表示されないことがあるバグがあります。 ボタンが表示されない場合は、ウィンドウが表示されるまでサイズを変更します。

1. 「 **[!UICONTROL ワークスペース]**」をクリックします。
1. プロジェクト内の `ADBMobileConfig.json` ファイルを探し、「 **[!UICONTROL OK]**」をクリックします。

アプリケーションは、を使用して、ライブラリからクラス/インターフェイスをインポ `adobeMobileLibrary.jar` ートでき `#include <ADBMobile.hpp>`ます。

## アプリの権限の追加

プロジェクトディレクトリ `bar-descriptor.xml` で行を追加 `<permission>access_internet</permission>`するか、QNX Momentics IDEで、「 **[!UICONTROL Application]** (アプリケーション **[!UICONTROL )」タブの権限セクションの「Internet]** （インターネット）」ボックスを選択します。

## 設定ファイルの `ADBMobileConfig.json` 更新

この `ADBMobileConfig.json` ファイルには、グローバルSDK設定が含まれています。 開始するには、いくつかの値を更新する必要があります。

The following is an example of an `ADBMobileConfig.json` file:

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

とのパラメーターは、少なくとも更新する必要 `rsids` があり `server` ます。 詳しくは、「 [AdobeMobileクラスとメソッドリファレンス](/help/blackberry/methods.md)」を参照してください。

BlackBerry 10アプリでAnalyticsを実装できるようになりました。
