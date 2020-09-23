---
description: 'null'
seo-description: 'null'
seo-title: 開発者向けクイックスタート
solution: Experience Cloud,Analytics
title: 開発者向けクイックスタート
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# 開発者向けクイックスタート{#developer-quick-start}

ユニバーサルWindowsプラットフォームライブラリの実装方法に関する情報を以下に示します。

>[!IMPORTANT]
>
>SDKを実装するには、Visual Studio 2013以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

SDKダウンロード [ファイルを解凍すると](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 、サポートされるアーキテクチャとプラットフォームの組み合わせごとに別々のフォルダーが作成されます。 また、 `ADBMobileConfig.json` ファイルも作成されます。 このファイルについて詳しくは、ADBMobileConfig.json設定ファイルを参照して [ください](/help/universal-windows/c-configuration/c.json.md)。

## 正しいバージョンを選択します {#section_E53C5AA7D5474824A89BB32C003865A1}

サポートされるアーキテクチャ(x86、x64、ARM)ごとに異なる `.dll/.winmd` ファイルが提供されます。

>[!IMPORTANT]
>
>のバージョンは、ライブラリのバージョン `ADBMobile.winmd` を反映していません。 フ `.winmd` ァイルにはメタデータのみが含まれ、バージョン番号はMicrosoftが受け入れる動作 `255.255.255.255`です。 詳細については、「 WinRT C++ / CXコンポーネントDLL用のアセンブリ情報を追加する [方法を教えてください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)に対する質問に回答します。使用しているライブラリのバージョンを確認するには、基になる `ADBMobile.dll` ファイルのバージョンを確認します。

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

ユニバーサルWindowsプラットフォームライブラリは、複数のプログラミング言語で使用できます。 このガイドの例はWinJS (JavaScript)で紹介されています。異なる言語を使用している場合は、変更が必要になる場合があります。 winJSからwinmdメソッドを使用する場合、すべてのメソッドの先頭文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。 また、WinJSプロジェクトでSDKを使用する場合は、空の文字列値ではなく空の文字列( `""` または `''`) `null` を使用します。

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studioを起動し、ソリューションを開きます。
1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルを参照します。

   詳しくは、このページの「正しいバージョン *を選択* 」セクションを参照してください。

1. 「**追加**」をクリックします。

1. 「 **[!UICONTROL 参照マネージャー]** 」(Reference Manager)ウィンドウでADBMobile.winmdファイルがチェック済みであることを確認し、「 **[!UICONTROL OK]**」をクリックします。

1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

   ソリューションにC++プロジェクトも存在する場合は、この手順をスキップします。

1. 左側の「 **[!UICONTROL Windows]** 」タブで、「 **[!UICONTROL Extensions]**」を選択し、「 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**」を選択して追加します。

1. クラス追加に次の行を追加します。

   ```csharp
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目をクリックします]**。

1. ファイルを参照し、 `ADBMobileConfig.json` をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. 「 **[!UICONTROL ビルドアクション]** 」を「 **[!UICONTROL コンテンツ]**」に変更します。

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studioを起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラーで]**、プロジェクトを右クリックし、 **** / **[!UICONTROL 参照を選択します]**。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルに参照を追加します。

   詳しくは、このページの「正しいバージョン *を選択* 」セクションを参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 「 `ADBMobile.winmd` 参照マネージャ **[!UICONTROL 」(]** Reference Manager **[!UICONTROL )ウィンドウでがチェック済みであることを確認し、「]** OK」をクリックします。

1. クラス追加に次の行を追加します。

   ```c++
   using namespace ADBMobile;
   ```

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目を選択します]**。

1. フ `ADBMobileConfig.json` ァイルを参照し、をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. 「 **[!UICONTROL General]** ( **[!UICONTROL 一般]** )」タブで、「 **[!UICONTROL Content]** （内容）」を「 **[!UICONTROL Yes（はい）」に変更し、「]** OK」をクリックします。

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studioを起動し、ソリューションを開きます。

1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルを参照します。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 「 **[!UICONTROL 参照マネージャー]** 」(Reference Manager)ウィンドウでADBMobile.winmdファイルがチェック済みであることを確認し、「 **[!UICONTROL OK]**」をクリックします。

1. ソリュ **[!UICONTROL ーションエクスプローラーで]**、「 **[!UICONTROL 参照」を右クリックし]** 、「参照 ****」を選択します。

   ソリューションにC++プロジェクトも存在する場合は、この手順をスキップします。

1. 左側の「 **[!UICONTROL Windows]** 」タブで、「 **[!UICONTROL Extensions]** 」を選択し、「 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**」を選択して追加します。

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 既存の項目を選択します]**。

1. ファイルを参照し、 `ADBMobileConfig.json` をクリックし **[!UICONTROL ます]**。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、「 **[!UICONTROL Properties]**」を選択します。

1. 「 **[!UICONTROL File Properties]** 」を選択した状態で、「 **[!UICONTROL Package Action]** 」が「 **[!UICONTROL Content]**」に設定されていることを確認します。

   JavaScriptプロジェクトの場合、ファイルはデフォルトで「コンテンツ」に設定されます。

## ADBMobileConfig.json設定ファイルの更新 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

この `ADBMobileConfig.json` ファイルは、グローバルSDK設定を含み、ライブラリと設定ファイルの手順を完了した後、プロジェクトルートに配置されます。こ *のファイルは、プロジェクトセクションに対す* るライブラリと設定ファイルの場所です。 AdobeのMobile Servicesによって `ADBMobileConfig.json` ファイルが事前設定されていない場合は、いくつかの値を更新して開始する必要があります。

`ADBMobileConfig.json` ファイルの例を次に示します。

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

* **Adobe Analytics**: `rsids` と `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDKのデバッグを有効にするには、を呼び出し `ADBMobile.Config.setDebugLogging(true);`ます。

C SharpおよびJavaScriptアプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります（C++アプリのデフォルト設定はネイティブコードのデバッグです）。

### Cシャープ

1. プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** /「 **[!UICONTROL デバッグ」タブをクリックします]**。

1. デバッガータイプのドロップダウンを「 **ネイティブのみ**」に変更します。

### JavaScript

1. プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** / **[!UICONTROL 設定プロパティ]** / **[!UICONTROL デバッグタブをクリックします]**。

1. デバッガータイプのドロップダウンを「 **[!UICONTROL ネイティブのみ]**」に変更します。

これで作業は完了です。これで、ユニバーサルWindowsプラットフォームアプリにAnalytics、ターゲット、オーディエンス管理を実装する準備が整いました。

