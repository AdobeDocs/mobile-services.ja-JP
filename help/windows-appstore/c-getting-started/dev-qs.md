---
description: 'null'
seo-description: 'null'
seo-title: 開発者向けクイックスタート
solution: Experience Cloud,Analytics
title: 開発者向けクイックスタート
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---

# 開発者向けクイックスタート {#developer-quick-start}

SDKを実装するには、Visual Studio 2013以降が必要です。

## SDK の取得  {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDKダウンロード](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)を解凍すると、サポートされるアーキテクチャとプラットフォームの組み合わせごとに個別のフォルダーが作成されます。 `ADBMobileConfig.json`ファイルも用意されています。このファイルについては、このガイドで後述します。

## 正しいバージョンを選択{#section_E53C5AA7D5474824A89BB32C003865A1}

各ターゲットプラットフォーム(Windows 8.1、Windows Phone 8.1)に異なる`.dll`/ `.winmd`ファイルが提供され、サポートされるアーキテクチャ(x86、x64、ARM)。 ファイルは、次の手順に従ってフォルダー構造に分けられます。

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>`ADBMobile.winmd`のバージョンは、ライブラリのバージョンを反映していません。 `.winmd`ファイルにはメタデータのみが含まれているので、`255.255.255.255`のバージョン番号はMicrosoftに従って受け入れられます（[WinRT C++ / CXコンポーネントDLLのアセンブリ情報を追加する方法を参照してください）。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) ）サードパーティリクエストを待機する、特別なコア Adobe JavaScript モジュールです。使用しているライブラリのバージョンを確認するには、基になる`ADBMobile.dll`ファイルのバージョンを確認します。

## 構文の違い{#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1ユニバーサルアプリストアライブラリは、複数のプログラミング言語で使用できます。 このガイドの例はWinJS (JavaScript)で紹介されており、異なる言語を使用する場合は変更が必要になる場合があります。 winJS (JavaScript)からwinmdメソッドを使用する場合、すべてのメソッドの先頭文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。

また、WinJSプロジェクトでSDKを使用する場合、空の文字列値には`null`ではなく空の文字列（`""`または`''`）を使用します。

## プロジ追加ェクトに対するライブラリと設定ファイル — C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studioを起動し、ソリューションを開きます。
1. **ソリューションエクスプローラー**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

1. ライブラリの正しいバージョンを選択し、関連する`ADBMobile.winmd`ファイルを参照します。

   詳しくは、下の&#x200B;*正しいバージョンを選択*&#x200B;の節を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウで`ADBMobile.winmd`が選択されていることを確認し、「**[!UICONTROL OK]**」をクリックします。

   >[!NOTE]
   >
   >Windows Phoneアプリに参照を追加する場合、`ADBMobile.winmd`を選択するには、既定のファイルフィルターを&#x200B;**[!UICONTROL コンポーネントファイル]**&#x200B;から&#x200B;**すべてのファイル**&#x200B;に変更します。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の&#x200B;**Windows**&#x200B;タブで、「**[!UICONTROL 拡張子]**」を選択し、**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**&#x200B;を選択して追加します。

1. クラス追加に次の行を追加します。

   ```
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューションの`ADBMobileConfig.json`ファイルを右クリックし、**[!UICONTROL プロパティ]**&#x200B;を選択します。

1. **[!UICONTROL ビルドアクション]**&#x200B;を&#x200B;**[!UICONTROL コンテンツ]**&#x200B;に変更します。

## プロジェクト追加のライブラリと設定ファイル — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studioを起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 参照]**&#x200B;を選択します。

1. ライブラリの正しいバージョンを選択し、関連する`ADBMobile.winmd`ファイルに参照を追加します。

   詳しくは、下の&#x200B;*正しいバージョンを選択*&#x200B;の節を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウで、`ADBMobile.winmd`が選択されていることを確認し、「**[!UICONTROL OK]**」をクリックします。

   >[!TIP]
   >
   >Windows Phoneアプリに参照を追加する場合、`ADBMobile.winmd`を選択するには、既定のファイルフィルターを&#x200B;**[!UICONTROL コンポーネントファイル]**&#x200B;から&#x200B;**すべてのファイル**&#x200B;に変更します。

1. クラス追加に次の行を追加します。

   ```
   using namespace ADMS::Measurement;
   ```

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューションの`ADBMobileConfig.json`ファイルを右クリックし、**[!UICONTROL プロパティ]**&#x200B;を選択します。

1. 「**[!UICONTROL 一般]**」タブで、**[!UICONTROL コンテンツ]**&#x200B;を&#x200B;**[!UICONTROL はい]**&#x200B;に変更し、**[!UICONTROL OK]**&#x200B;をクリックします。

## プロジ追加ェクトに対するライブラリと設定ファイル — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studioを起動し、ソリューションを開きます。
1. **ソリューションエクスプローラー**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

   詳しくは、*下の「正しいバージョン*」を参照してください。

1. ライブラリの正しいバージョンを選択し、関連する`ADBMobile.winmd`ファイルを参照します。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. **[!UICONTROL 参照マネージャー]**&#x200B;ウィンドウで`ADBMobile.winmd`がチェック済みであることを確認し、「**[!UICONTROL OK]**」をクリックします。

   >[!TIP]
   >
   >Windows Phoneアプリに参照を追加する場合、`ADBMobile.winmd`を選択するには、既定のファイルフィルターを&#x200B;**[!UICONTROL コンポーネントファイル]**&#x200B;から&#x200B;**すべてのファイル**&#x200B;に変更します。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、**[!UICONTROL 「参照」]**&#x200B;を右クリックし、「**[!UICONTROL 追加参照]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の&#x200B;**[!UICONTROL Windows]**&#x200B;タブで、「**[!UICONTROL 拡張子]**」を選択し、**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**&#x200B;を選択して追加します。

1. プロジェクトを右クリックし、**[!UICONTROL 追加]**/**[!UICONTROL 既存の項目]**&#x200B;を選択します。

1. `ADBMobileConfig.json`ファイルを参照し、**[!UICONTROL 追加]**&#x200B;をクリックします。

1. ソリューションの`ADBMobileConfig.json]`ファイルを右クリックし、**[!UICONTROL プロパティ]**&#x200B;を選択します。

1. 「**[!UICONTROL ファイルプロパティ]**」を選択した状態で、「**[!UICONTROL パッケージアクション]**」が「**[!UICONTROL コンテンツ]**」に設定されていることを確認します。

   JavaScriptプロジェクトの場合、ファイルはデフォルトで&#x200B;**[!UICONTROL Content]**&#x200B;に設定されます。

## ADBMobileConfig.json設定ファイル{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}を更新します。

`ADBMobileConfig.json`ファイルは、グローバルSDK設定を含み、*プロジェクト*&#x200B;セクションのライブラリと設定ファイルの手順を完了す追加ると、プロジェクトルートに配置されます。 `ADBMobileConfig.json`ファイルがAdobeのMobile Servicesによって事前設定されていない場合、開始するには、いくつかの値を更新する必要があります。

次に`ADBMobileConfig.json`ファイルの例を示します。

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

* **解析**: `rsids` と  `server`
* **Target**: `clientCode`
* **オーディエンス管理**:  `server`

詳しくは、[ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md)を参照してください。

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDKのデバッグを有効にする場合は、`ADBMobile.Config.setDebugLogging(true);`を呼び出す必要があります。

C SharpおよびJSアプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります（ネイティブコードのデバッグはC++アプリのデフォルト設定です）。

### Cシャープ

プロジェクトを右クリックし、**[!UICONTROL プロパティ]**/**[!UICONTROL デバッグタブ]**&#x200B;を選択します。 「デバッガー」ドロップダウンで、「**[!UICONTROL ネイティブのみ]**」を選択します。

### JS

プロジェクトを右クリックし、**[!UICONTROL プロパティ]**/**[!UICONTROL 構成プロパティ]**/**[!UICONTROL デバッグタブ]**&#x200B;を選択します。 デバッガーのタイプのドロップダウンを&#x200B;**ネイティブのみ**&#x200B;に変更します。

これで作業は完了です。これで、Windows 8.1ユニバーサルアプリストアアプリにAnalytics、ターゲット、オーディエンス管理を実装する準備が整いました。
