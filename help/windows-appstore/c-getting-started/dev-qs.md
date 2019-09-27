---
description: 'null'
seo-description: 'null'
seo-title: 開発者クイックスタート
solution: Marketing Cloud,Analytics
title: 開発者クイックスタート
topic: 開発者と導入
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

SDK を実装するには、Visual Studio 2013 以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

[SDK ダウンロードファイル](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)を解凍すると、サポートされているアーキテクチャとプラットフォームの組み合わせごとに異なるフォルダーが作成されます。また、このガイドで説明されている `ADBMobileConfig.json` ファイルも含まれています。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). ファイルは、次の構造に従って異なるフォルダーに配置されています。

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) を参照してください）。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 ユニバーサルアプリストアライブラリは、複数のプログラミング言語で使用できます。このガイドでは WinJS（JavaScript）の例を取り上げていますが、別の言語を使用する場合は変更が必要な可能性があります。winJS（JavaScript）から winmd メソッドを使用する場合、すべてのメソッドの 1 文字目が自動的に小文字に変換されるので注意が必要です。

実装間の主な違いは、コンテキストデータに使用するデータ構造です。

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   詳しくは、以下の「正しいバージ *ョンを選択* 」を参照してください。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Windows phoneアプリへの参照を追加する際に、デフォルトのファイルフィルタ `ADBMobile.winmd`ーを「コンポーネントファイル」から「すべ **[!UICONTROL てのファ]** イル **」に変更します**。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **「** Windows **[!UICONTROL 」タブで、「]** Extensions **[!UICONTROL 」を選択し、「]** Microsoft Visual C++ 2013 Runtime Package for Windows」を選択して追加します。

1. クラスに次の行を追加します。

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to your `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   詳しくは、以下の「正しいバージ *ョンを選択* 」を参照してください。

1. Click **[!UICONTROL Add]**.

1. 「参照マネ **[!UICONTROL ージャ]** 」(Reference Manager `ADBMobile.winmd` )ウィンドウで、が選択され **[!UICONTROL ていることを確認し、「]** OK」をクリックします。

   >[!TIP]
   >
   >Windows phoneアプリへの参照を追加する際に、デフォルトのファイルフィルタ `ADBMobile.winmd`ーを「コンポーネントファイル」から「すべ **[!UICONTROL てのファ]** イル **」に変更します**。

1. クラスに次の行を追加します。

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   詳しくは、以下の「正しいバージ *ョンを選択* 」を参照してください。

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >When adding a reference to a Windows Phone app, to select , change the default file filter from Component Files to All Files.`ADBMobile.winmd`********

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **[!UICONTROL 「]** Windows **[!UICONTROL 」タブで、「]** Extensions **[!UICONTROL 」を選択し、「]** Microsoft Visual C++ 2013 Runtime Package for Windows」を選択して追加します。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. 「 **[!UICONTROL File Properties]** 」を選択し、「 **[!UICONTROL Package Action]** 」が「 **[!UICONTROL Content」に設定されていることを確認します]**。

   For JavaScript projects, the file is set to Content by default.****

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

使用しているソリューションに応じて、少なくとも次の値を更新する必要があります。

* **Analytics:  and**`rsids``server`
* **Target**: `clientCode`
* **Audience Management**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK に対してデバッグを有効にするには、`ADBMobile.Config.setDebugLogging(true);` ); を呼び出す必要があります。

For C Sharp and JS apps, you have to enable native code debugging by completing the following steps (native code debugging is the default setting for C++ apps):

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. 「デバッガー」ドロップダウンで、「ネイティブの **[!UICONTROL み」を選択しま]**&#x200B;す。

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. デバッガタイプのドロップダウンリストを「**Native Only（ネイティブのみ）**」に変更します。

これで作業は完了です。Windows 8.1 ユニバーサルアプリストアアプリケーションで Analytics、Target および Audience Management を実装する準備は以上です。
