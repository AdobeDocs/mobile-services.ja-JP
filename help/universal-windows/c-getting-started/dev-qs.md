---
description: ユニバーサルWindowsプラットフォームライブラリの実装方法に関する情報です。
solution: Experience Cloud,Analytics
title: 開発者向けクイックスタート
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# 開発者向けクイックスタート{#developer-quick-start}

ユニバーサルWindowsプラットフォームライブラリの実装方法に関する情報を以下に示します。

>[!IMPORTANT]
>
>SDKを実装するには、Visual Studio 2013以降が必要です。

## SDK の取得  {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDKダウンロード](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)ファイルを解凍すると、サポートされるアーキテクチャとプラットフォームの組み合わせごとに個別のフォルダーが作成されます。 `ADBMobileConfig.json`ファイルも持っています。 このファイルについて詳しくは、[ADBMobileConfig.json config file](/help/universal-windows/c-configuration/c.json.md)を参照してください。

## 正しいバージョンを選択{#section_E53C5AA7D5474824A89BB32C003865A1}

サポートされるアーキテクチャ(x86、x64、ARM)ごとに異なる`.dll/.winmd`ファイルが提供されます。

>[!IMPORTANT]
>
>`ADBMobile.winmd`のバージョンは、ライブラリのバージョンを反映していません。 `.winmd`ファイルにはメタデータのみが含まれ、バージョン番号は`255.255.255.255`で、Microsoftの規定に従って受け入れられます。 詳細については、[WinRT C++ / CXコンポーネントdllのアセンブリ情報を追加する方法を参照してください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)に対する質問に回答します。使用しているライブラリのバージョンを確認するには、基になる`ADBMobile.dll`ファイルのバージョンを確認します。

## 構文の違い{#section_A02DE120B6D240F5AFFE7509755C4F14}

ユニバーサルWindowsプラットフォームライブラリは、複数のプログラミング言語で使用できます。 このガイドの例はWinJS (JavaScript)で紹介されています。異なる言語を使用している場合は、変更が必要になる場合があります。 winJSからwinmdメソッドを使用する場合、すべてのメソッドの先頭文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。 また、WinJSプロジェクトでSDKを使用する場合、空の文字列値には`null`ではなく空の文字列（`""`または`''`）を使用します。

## ライブラリ追加と設定ファイルをプロジェクトに — C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studioを起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルを参照します。

   詳しくは、このページの「*正しいバージョンを選択*」を参照してください。

1. 「**追加**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウでADBMobile.winmdファイルがチェック済みであることを確認し、「**[!UICONTROL OK]**」をクリックします。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

   ソリューションにC++プロジェクトも存在する場合は、この手順をスキップします。

1. 左側の&#x200B;**[!UICONTROL Windows]**&#x200B;タブで、「**[!UICONTROL 拡張子]**」を選択し、**[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**&#x200B;を選択して追加します。

1. クラス追加に次の行を追加します。

   ```csharp
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;をクリックします。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューション内の`ADBMobileConfig.json`ファイルを右クリックし、「**[!UICONTROL プロパティ]**」を選択します。

1. **[!UICONTROL ビルドアクション]**&#x200B;を&#x200B;**[!UICONTROL コンテンツ]**&#x200B;に変更します。

## プロジェクト追加のライブラリと設定ファイル — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studioを起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 参照]**&#x200B;を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルに参照を追加します。

   詳しくは、このページの「*正しいバージョンを選択*」を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウで`ADBMobile.winmd`がチェック済みであることを確認し、「**[!UICONTROL OK]**」をクリックします。

1. クラス追加に次の行を追加します。

   ```c++
   using namespace ADBMobile;
   ```

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューションの`ADBMobileConfig.json`ファイルを右クリックし、**[!UICONTROL プロパティ]**&#x200B;を選択します。

1. 「**[!UICONTROL 一般]**」タブで、**[!UICONTROL コンテンツ]**&#x200B;を&#x200B;**[!UICONTROL はい]**&#x200B;に変更し、**[!UICONTROL OK]**&#x200B;をクリックします。

## プロジ追加ェクトに対するライブラリと設定ファイル — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studioを起動し、ソリューションを開きます。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile.winmdファイルを参照します。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウでADBMobile.winmdファイルがチェック済みであることを確認し、「**[!UICONTROL OK]**」をクリックします。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

   ソリューションにC++プロジェクトも存在する場合は、この手順をスキップします。

1. 左側の&#x200B;**[!UICONTROL Windows]**&#x200B;タブで、「**[!UICONTROL 拡張子]**」を選択し、**[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**&#x200B;を選択して追加します。

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューションの`ADBMobileConfig.json`ファイルを右クリックし、**[!UICONTROL プロパティ]**&#x200B;を選択します。

1. 「**[!UICONTROL ファイルプロパティ]**」を選択した状態で、「**[!UICONTROL パッケージアクション]**」が「**[!UICONTROL コンテンツ]**」に設定されていることを確認します。

   JavaScriptプロジェクトの場合、ファイルはデフォルトで「コンテンツ」に設定されます。

## ADBMobileConfig.json設定ファイル{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}の更新

`ADBMobileConfig.json`ファイルは、グローバルSDK設定を含み、プロジェクトルートに配置されます。このファイルは、ライブラリと設定ファイルの&#x200B;*内の手順を完了す追加ると、プロジェクト*&#x200B;セクションに配置されます。 `ADBMobileConfig.json`ファイルがAdobeのMobile Servicesによって事前設定されていない場合、開始するには、いくつかの値を更新する必要があります。

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

* **Adobe Analytics**: `rsids` と  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

詳しくは、[SDKメソッド](/help/universal-windows/c-configuration/methods.md)を参照してください。

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDKのデバッグを有効にするには、`ADBMobile.Config.setDebugLogging(true);`を呼び出します。

C SharpおよびJavaScriptアプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります（C++アプリのデフォルト設定はネイティブコードのデバッグです）。

### Cシャープ

1. プロジェクトを右クリックし、**[!UICONTROL プロパティ]**/**[!UICONTROL デバッグタブ]**&#x200B;をクリックします。

1. デバッガーのタイプのドロップダウンを&#x200B;**ネイティブのみ**&#x200B;に変更します。

### JavaScript

1. プロジェクトを右クリックし、**[!UICONTROL プロパティ]**/**[!UICONTROL 構成プロパティ]**/**[!UICONTROL デバッグタブ]**&#x200B;をクリックします。

1. デバッガーのタイプのドロップダウンを&#x200B;**[!UICONTROL ネイティブのみ]**&#x200B;に変更します。

これで作業は完了です。これで、ユニバーサルWindowsプラットフォームアプリにAnalytics、ターゲット、オーディエンス管理を実装する準備が整いました。
