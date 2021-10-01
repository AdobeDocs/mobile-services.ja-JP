---
title: 開発者クイックスタート
description: 『BlackBerry 開発者クイックスタートガイド』は、Mobile Services 用の BlackBerry ライブラリを実装するプロセスを理解するのに役立ちます。
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 6%

---

# 開発者向けクイックスタート

この情報は、BlackBerry ライブラリを実装するプロセスを理解するのに役立ちます。

## SDK の取得

**SDK には BlackBerry 10 以降が必要です。**

ダウンロードした SDK を解凍したら、`AdobeMobile` フォルダーに次のファイルが存在することを確認します。

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

1. プロジェクトを右クリックし、**[!UICONTROL 設定]** / **[!UICONTROL ライブラリを追加]** を選択します。
1. 「**[!UICONTROL 外部ライブラリ]**」を選択し、「**[!UICONTROL 次へ]**」をクリックします。
1. 「**[!UICONTROL デバイスライブラリ]**」フィールドの横にある「**[!UICONTROL 参照]**」をクリックします。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. `Device-Debug` フォルダーで `libADBMobileShared.so` を選択し、**[!UICONTROL 「]** を開く」をクリックします。
1. 「**[!UICONTROL シミュレーターライブラリ]**」フィールドの横にある「**[!UICONTROL 参照]**」をクリックします。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. `Device-Debug` フォルダーで `libADBMobileShared.so` を選択し、**[!UICONTROL 「]** を開く」をクリックします。
1. 「**[!UICONTROL フォルダーを含める]**」フィールドの横にある「**[!UICONTROL 追加]**」をクリックします。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーに移動し、
1. `public` フォルダーをインクルードに追加します。
1. `ADBMobile-4.0.0BETA-BlackBerry` フォルダーには、`ADBMobileConfig.json` という名前の `.json` 設定ファイルがあります。

   そのファイルをプロジェクトのルートにコピーします。
1. プロジェクトを右クリックし、「**[!UICONTROL 更新]**」を選択します。

   これで、`.json` ファイルが **[!UICONTROL プロジェクトエクスプローラー]** に表示されます。
1. プロジェクトの `bar-descriptor.xml` ファイルを開きます。
1. ウィンドウの下部で、「**[!UICONTROL アセット]**」タブを選択します。
1. **[!UICONTROL (All Configurations)]** が選択されていることを確認し、ウィンドウの **[!UICONTROL Assets]** セクションで「**[!UICONTROL ファイルを追加]**」をクリックします。
   >[!TIP]
   >
   >QNX Momentics IDE には、これらのボタンが表示されないバグがあります。 ボタンが表示されない場合は、表示されるまでウィンドウのサイズを変更します。

1. 「**[!UICONTROL ワークスペース]**」をクリックします。
1. プロジェクト内の `ADBMobileConfig.json` ファイルを探し、「**[!UICONTROL OK]**」をクリックします。

アプリケーションは、`#include <ADBMobile.hpp>` を使用して `adobeMobileLibrary.jar` ライブラリからクラス/インターフェイスを読み込むことができます。

## アプリの権限の追加

プロジェクトディレクトリの `bar-descriptor.xml` に行 `<permission>access_internet</permission>` を追加するか、QNX Momentics IDE で、「**[!UICONTROL Application]**」タブの「permissions」セクションの「**[!UICONTROL Internet]**」ボックスを選択します。

## `ADBMobileConfig.json` 設定ファイルを更新します。

`ADBMobileConfig.json` ファイルには、グローバル SDK 設定が含まれています。 使い始めるには、いくつかの値を更新する必要があります。

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

`rsids` パラメーターと `server` パラメーターを少なくとも更新する必要があります。 詳しくは、[Adobeモバイルクラスとメソッドのリファレンス ](/help/blackberry/methods.md) を参照してください。

BlackBerry 10 アプリに Analytics を実装できるようになりました。
