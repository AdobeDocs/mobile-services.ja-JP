---
description: 'null'
seo-description: 'null'
seo-title: 開発者向けクイックスタート
solution: Experience Cloud,Analytics
title: 開発者向けクイックスタート
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---


# 開発者向けクイックスタート {#developer-quick-start}

SDKを実装するには、Visual Studio 2013以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

SDKダウンロードを解凍すると [](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)、サポートされるアーキテクチャとプラットフォームの組み合わせごとに別々のフォルダーが作成されます。 また、このガイドで後ほど説明する `ADBMobileConfig.json` ファイルも用意されています。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

ターゲットプラットフォーム(Windows 8.1、Windows Phone 8.1)およびサポートされるアーキテクチャ(x86、x64、ARM)ごとに異なる `.dll`/ `.winmd` ファイルが提供されます。 ファイルは、次の手順に従ってフォルダー構造に分けられます。

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>のバージョンは、ライブラリのバージョン `ADBMobile.winmd` を反映していません。 フ `.winmd` ァイルにはメタデータのみが含まれ、Microsoftに従って許可されるバージョン番号が含まれます( `255.255.255.255`[WinRT C++ / CXコンポーネントdll用のアセンブリ情報を追加する方法を参照してください)。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) ）サードパーティリクエストを待機する、特別なコア Adobe JavaScript モジュールです。使用しているライブラリのバージョンを確認するには、基になる `ADBMobile.dll` ファイルのバージョンを確認します。

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1ユニバーサルアプリストアライブラリは、複数のプログラミング言語で使用できます。 このガイドの例はWinJS (JavaScript)で紹介されており、異なる言語を使用する場合は変更が必要になる場合があります。 winJS (JavaScript)からwinmdメソッドを使用する場合、すべてのメソッドの先頭文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。

また、WinJSプロジェクトでSDKを使用する場合は、空の文字列値ではなく空の文字列( `""` または `''`) `null` を使用します。

## プロジェクト追加へのライブラリと設定ファイル — C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studioを起動し、ソリューションを開きます。
1. ソリュ **ーションエクスプローラーで**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイルを参照します。

   詳しくは、下の「正しいバージョンを *選択* 」を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 「 `ADBMobile.winmd` 参照マネージャ **[!UICONTROL 」(]** Reference Manager **[!UICONTROL )ウィンドウでが選択されていることを確認し、「]** OK」をクリックします。

   >[!NOTE]
   >
   >Windows Phoneアプリに参照を追加する場合、選択するに `ADBMobile.winmd`は、デフォルトのファイルフィルタを「 **[!UICONTROL コンポーネントファイル]****」から「**&#x200B;すべてのファイル」に変更します。

1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **「Windows** 」タブで、「 **[!UICONTROL Extensions]**」を選択し、「 **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**」を選択して追加します。

1. クラス追加に次の行を追加します。

   ```
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. フ `ADBMobileConfig.json` ァイルを参照し、をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. 「 **[!UICONTROL ビルドアクション]** 」を「 **[!UICONTROL コンテンツ]**」に変更します。

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studioを起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラーで]**、プロジェクトを右クリックし、 **** / **[!UICONTROL 参照を選択します]**。

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイルに参照を追加します。

   詳しくは、下の「正しいバージョンの *選択* 」の節を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 「 **[!UICONTROL 参照マネージャ]** 」(Reference Manager `ADBMobile.winmd` )ウィンドウで、が選択されていることを確認し **[!UICONTROL 、「]** OK」をクリックします。

   >[!TIP]
   >
   >Windows Phoneアプリに参照を追加する場合、選択するに `ADBMobile.winmd`は、デフォルトのファイルフィルタを「 **[!UICONTROL コンポーネントファイル]****」から「**&#x200B;すべてのファイル」に変更します。

1. クラス追加に次の行を追加します。

   ```
   using namespace ADMS::Measurement;
   ```

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. ファイルを参照し、 `ADBMobileConfig.json` をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. [ **[!UICONTROL 一般]** ]タブで、[ **[!UICONTROL コンテンツ]** ]を **[!UICONTROL [はい]**]に変更し、[ **** OK]をクリックします。

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studioを起動し、ソリューションを開きます。
1. ソリュ **ーションエクスプローラーで**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

   詳しくは、下の「正しいバージョンを *選択* 」を参照してください。

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイルを参照します。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 「 `ADBMobile.winmd` 参照マネージャ **[!UICONTROL 」(]** Reference Manager **[!UICONTROL )ウィンドウでがチェック済みであることを確認し、「]** OK」をクリックします。

   >[!TIP]
   >
   >Windows Phoneアプリに参照を追加する場合、選択するに `ADBMobile.winmd`は、デフォルトのファイルフィルタを「 **[!UICONTROL コンポーネントファイル]****」から「**&#x200B;すべてのファイル」に変更します。

1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **[!UICONTROL 「Windows]** 」タブで、「 **[!UICONTROL Extensions]** 」を選択し、「 **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**」を選択して追加します。

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目を選択します]**。

1. ファイルを参照し、 `ADBMobileConfig.json` をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json]` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. 「 **[!UICONTROL File Properties]** 」を選択した状態で、「 **[!UICONTROL Package Action]** 」が「 **[!UICONTROL Content]**」に設定されていることを確認します。

   JavaScriptプロジェクトの場合、ファイルはデフォルトで **[!UICONTROL Content]** に設定されます。

## ADBMobileConfig.json設定ファイルの更新 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

この `ADBMobileConfig.json` ファイルには、グローバルSDK設定が含まれており、ライブラリと設定ファイルの手順を完了した後、プロジェクトルートに配置されます。こ *のファイルは、プロジェクト* セクションに対するライブラリと設定ファイルの場所です。 AdobeのMobile Servicesによって `ADBMobileConfig.json` ファイルが事前設定されていない場合は、いくつかの値を更新して開始する必要があります。

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

少なくとも、使用しているソリューションに対して次の値を更新してください。

* **解析**: `rsids` と `server`
* **Target**: `clientCode`
* **オーディエンス管理**: `server`

詳しくは、ADBMobileConfig.json config [を参照してください](/help/windows-appstore/c-configuration/methods.md)。

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDKのデバッグを有効にする場合は、を呼び出す必要があり `ADBMobile.Config.setDebugLogging(true);`ます。

C SharpおよびJSアプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります（ネイティブコードのデバッグはC++アプリのデフォルト設定です）。

### Cシャープ

プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** /「 **[!UICONTROL デバッグ」タブを選択します]**。 「デバッガー」ドロップダウンで、「 **[!UICONTROL ネイティブのみ]**」を選択します。

### JS

プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** / **[!UICONTROL 設定プロパティ]** / **[!UICONTROL デバッグタブを選択します]**。 デバッガータイプのドロップダウンを「 **ネイティブのみ**」に変更します。

これで作業は完了です。これで、Windows 8.1ユニバーサルアプリストアアプリにAnalytics、ターゲット、オーディエンス管理を実装する準備が整いました。
