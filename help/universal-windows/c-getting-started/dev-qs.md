---
description: 'null'
seo-description: 'null'
seo-title: 開発者クイックスタート
solution: Marketing Cloud、Analytics
title: 開発者クイックスタート
topic: 開発者と導入
uuid: 11c06fcf- d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

ユニバーサルWindows Platformライブラリの実装方法について、以下に説明します。

>[!IMPORTANT]
>
>SDKを実装するには、Visual Studio2013以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDKダウンロード](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) ファイルの解凍後、サポートされているアーキテクチャとプラットフォームの組み合わせごとに、個別のフォルダーが表示されます。`ADBMobileConfig.json` ファイルもあります。このファイルについて詳しくは [、ADBMobileConfig. json configファイル](/help/universal-windows/c-configuration/c.json.md)を参照してください。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` ファイルにはメタデータのみが含まれており、バージョン `255.255.255.255`番号があります。これはMicrosoftに従って動作します。詳しくは、WinRT C++/CXコンポーネントdllのアセンブリ情報を追加 [する方法を参照してください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)をインストールします。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

Universal Windows Platform ライブラリは複数のプログラミング言語で使用できます。このガイドの例はWinJS（JavaScript）にあり、異なる言語を使用している場合、変更が必要な場合があります。WinJSのwinmdメソッドを使用すると、すべてのメソッドが自動的に最初の文字を小文字にします。

実装間の主な違いは、コンテキストデータに使用するデータ構造です。Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile. winmdファイルを参照します。

   詳しくは、このページの *「正しいバージョン* の選択」を参照してください。

1. 「**Add**」をクリックします。

1. **[!UICONTROL Reference Manager]** ウィンドウでADBMobile. winmdファイルがチェックされていることを確認し、 **[!UICONTROL "OK]**」をクリックします。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップしてください。

1. 左側の **[!UICONTROL "Windows]** 」タブで **[!UICONTROL 、「拡張機能]**」を選択し、「ユニバーサルWindowsプラットフォームアプリ用 **[!UICONTROL のVisual C++2015ランタイム」を選択して追加]**&#x200B;します。

1. クラスに次の行を追加します。

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. ソリューション内の `ADBMobileConfig.json` ファイルを右クリックし、 **[!UICONTROL 「プロパティ]**」を選択します。

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 参照を選択]**&#x200B;します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile. winmdファイルへの参照を追加します。

   詳しくは、このページの *「正しいバージョン* の選択」を参照してください。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. クラスに次の行を追加します。

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 「一般」]** タブで、「コンテンツ»を??«はい»??に??変更??し、??«OK??************

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

1. ライブラリの正しいバージョンを選択し、関連するADBMobile. winmdファイルを参照します。

1. Click **[!UICONTROL Add]**.

1. **[!UICONTROL Reference Manager]** ウィンドウでADBMobile. winmdファイルがチェックされていることを確認し、 **[!UICONTROL "OK]**」をクリックします。

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップしてください。

1. 左側の **[!UICONTROL "Windows]** 」タブで「拡張機能」を選択 **** し、「ユニバーサルWindowsプラットフォームアプリ用 **[!UICONTROL のVisual C++2015ランタイム」を選択して追加]**&#x200B;します。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. 「 **[!UICONTROL ファイルプロパティ»??を選択した状態で、??«パッケージアクション??]**********

   JavaScriptプロジェクトの場合、ファイルはデフォルトでコンテンツに設定されます。

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` ファイルにはグローバルSDK設定が含まれており、プロジェクト ** セクションにライブラリと設定ファイルを追加すると、プロジェクトルートに場所があります。If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

少なくとも、使用しているソリューションに対して以下の値を更新します。

* **Adobe Analytics**: `rsids` および `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

詳しくは [、SDKメソッド](/help/universal-windows/c-configuration/methods.md)を参照してください。

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDKのデバッグを有効にするには、を呼び出し `ADBMobile.Config.setDebugLogging(true);`ます。

CシャープおよびJavaScriptアプリの場合は、次の手順を実行してネイティブコードデバッグを有効にする必要があります（ネイティブコードデバッグは、C++アプリケーションのデフォルト設定です）。

### Cシャープ

1. プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** / **[!UICONTROL デバッグタブ]**&#x200B;をクリックします。

1. デバッガタイプのドロップダウンリストを「**Native Only（ネイティブのみ）**」に変更します。

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

これで作業は完了です。Universal Windows Platform アプリケーションで Analytics、Target、Audience Management を実装する準備は以上です。

