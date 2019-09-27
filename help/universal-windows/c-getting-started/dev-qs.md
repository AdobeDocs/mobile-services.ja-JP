---
description: 'null'
seo-description: 'null'
seo-title: 開発者クイックスタート
solution: Marketing Cloud,Analytics
title: Developer quick start
topic: 開発者と導入
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Here is some information about how to implement the Universal Windows Platform library.

>[!IMPORTANT]
>
>To implement the SDK, you need Visual Studio 2013 or later.

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. You will also have an  file. `ADBMobileConfig.json`このファイルについて詳しくは、 [ADBMobileConfig.json設定ファイルを参照してください](/help/universal-windows/c-configuration/c.json.md)。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. ファイ `.winmd` ルにはメタデータのみが含まれ、バージョン番号はの `255.255.255.255`みで、Microsoftが認める動作です。 詳細については、「 WinRT C++ / CX [コンポーネントdllのアセンブリ情報を追加する方法を教えてください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)をインストールします。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

Universal Windows Platform ライブラリは複数のプログラミング言語で使用できます。このガイドの例はWinJS (JavaScript)で紹介されています。異なる言語を使用している場合は、変更が必要になる場合があります。 When you consume winmd methods from winJS, all methods automatically have their first letter lowercased.

実装間の主な違いは、コンテキストデータに使用するデータ構造です。Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version  of the library and browse to the associated ADBMobile.winmd file.

   詳しくは、このページの「正し *いバージョンを選択* 」を参照してください。

1. 「**Add**」をクリックします。

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の「 **[!UICONTROL Windows]** 」タブで、「 **[!UICONTROL Extensions]**」を選択し、「 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps」を選択して追加します]**。

1. クラスに次の行を追加します。

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. ソリューション内のファイル `ADBMobileConfig.json` を右クリックし、「プロパティ」を選 **[!UICONTROL 択します]**。

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. 正しいバージョンのライブラリを選択し、関連するADBMobile.winmdファイルに参照を追加します。

   詳しくは、このページの「正し *いバージョンを選択* 」を参照してください。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. クラスに次の行を追加します。

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated ADBMobile.winmd file.

1. Click **[!UICONTROL Add]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の「 **[!UICONTROL Windows]** 」タブで、「 **[!UICONTROL Extensions]** 」を選択し、「 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps」を選択して追加します]**。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. 「 **[!UICONTROL File Properties]** 」を選択し、「 **[!UICONTROL Package Action]** 」が「 **[!UICONTROL Content」に設定されていることを確認します]**。

   For JavaScript projects, the file is set to Content by default.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

At a minimum, update the following values for the solutions you are using:

* **Adobe Analytics**: `rsids` and `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see SDK methods.[](/help/universal-windows/c-configuration/methods.md)

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

To enable debugging for the SDK, call .`ADBMobile.Config.setDebugLogging(true);`

C SharpおよびJavaScriptアプリの場合、次の手順でネイティブコードデバッグを有効にする必要があります（C++アプリのデフォルト設定はネイティブコードデバッグです）。

### C Sharp

1. Right-click the project, click  Properties &gt; Debug tab.********

1. デバッガタイプのドロップダウンリストを「**Native Only（ネイティブのみ）**」に変更します。

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

これで作業は完了です。Universal Windows Platform アプリケーションで Analytics、Target、Audience Management を実装する準備は以上です。

