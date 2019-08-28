---
description: 'null'
seo-description: 'null'
seo-title: 開発者クイックスタート
solution: Marketing Cloud、Analytics
title: 開発者クイックスタート
topic: 開発者と導入
uuid: b368959b- d985-436e-8b3e-97e355a97951
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
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` ファイルにはメタデータのみが含まれています。そのため、Microsoftに応じて受け入れられる動作のバージョン番号があります（WinRT `255.255.255.255` C++/CXコンポーネントdllのアセンブリ情報を追加 [する方法を参照してください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) を参照してください）。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 ユニバーサルアプリストアライブラリは、複数のプログラミング言語で使用できます。このガイドでは WinJS（JavaScript）の例を取り上げていますが、別の言語を使用する場合は変更が必要な可能性があります。winJS（JavaScript）から winmd メソッドを使用する場合、すべてのメソッドの 1 文字目が自動的に小文字に変換されるので注意が必要です。

実装間の主な違いは、コンテキストデータに使用するデータ構造です。

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. **ソリューションエクスプローラー**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UIUCONTROL Add Reference]**」を選択します。

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   詳しくは、以下の正しい *バージョン* の選択を参照してください。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Windows Phoneアプリケーションへの参照を追加するときに、 `ADBMobile.winmd`デフォルトのファイルフィルターを **[!UICONTROL 「コンポーネントファイル]** »から?«すべてのファイル?****

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **"Windows** 」タブで「拡張機能」を選択 ****&#x200B;し、Windows用の **[!UICONTROL Microsoft Visual C++2013ランタイムパッケージを選択して追加]**&#x200B;します。

1. クラスに次の行を追加します。

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で、プロジェクトを右クリックし、 **[!UICONTROL 追加]** / **[!UICONTROL 参照を選択]**&#x200B;します。

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   詳しくは、下記の「正しいバージョンの *選択」* を参照してください。

1. Click **[!UICONTROL Add]**.

1. **[!UICONTROL Reference Manager]** ウィンドウで、が選択されていることを確認 `ADBMobile.winmd` し、 **[!UICONTROL "OK]**」をクリックします。

   >[!TIP]
   >
   >Windows Phoneアプリケーションへの参照を追加するときに、 `ADBMobile.winmd`デフォルトのファイルフィルターを **[!UICONTROL 「コンポーネントファイル]** »から?«すべてのファイル?****

1. クラスに次の行を追加します。

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. **[!UICONTROL 「一般」]** タブで **[!UICONTROL 、「コンテンツ]** »を??«はい»??に変更し、??«OK??********

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。
1. **ソリューションエクスプローラー**&#x200B;で **[!UICONTROL 、"References]** 」を右クリックし **て[!UACROLの追加リファレンス**

   詳しくは、下記の「正しい *バージョン* の選択」を参照してください。

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Windows Phoneアプリケーションへの参照を追加するときに、 `ADBMobile.winmd`デフォルトのファイルフィルターを **[!UICONTROL 「コンポーネントファイル]** »から?«すべてのファイル?****

1. **[!UICONTROL ソリューションエクスプローラー]**&#x200B;で **[!UICONTROL 、"References"を右クリック]** し、「 **[!UICONTROL Add Reference]**」を選択します。

   ソリューションにC++プロジェクトもある場合は、この手順をスキップします。

1. 左側の **[!UICONTROL "Windows]** 」タブで「拡張機能」を選択 **** し、Windows用の **[!UICONTROL Microsoft Visual C++2013ランタイムパッケージを選択して追加]**&#x200B;します。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. `ADBMobileConfig.json` ファイルを参照し、 **[!UICONTROL 「追加]**」をクリックします。

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. 「 **[!UICONTROL ファイルプロパティ»??を選択した状態で、??«パッケージアクション??]**********

   JavaScriptプロジェクトの場合、ファイルはデフォルトで **[!UICONTROL コンテンツ]** に設定されます。

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` ファイルにはグローバルSDK設定が含まれており、プロジェクト ** セクションに「ライブラリと設定ファイルを追加」の手順を完了すると、プロジェクトルートに配置されます。If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

* **Analytics**: `rsids` および `server`
* **Target**: `clientCode`
* **Audience Management**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK に対してデバッグを有効にするには、`ADBMobile.Config.setDebugLogging(true);` ); を呼び出す必要があります。

CシャープおよびJSアプリケーションの場合は、次の手順を実行してネイティブコードデバッグを有効にする必要があります（ネイティブコードデバッグは、C++アプリケーションのデフォルト設定です）。

### Cシャープ

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. デバッガードロップダウンで、 **[!UICONTROL 「ネイティブのみ]**」を選択します。

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. デバッガタイプのドロップダウンリストを「**Native Only（ネイティブのみ）**」に変更します。

これで作業は完了です。Windows 8.1 ユニバーサルアプリストアアプリケーションで Analytics、Target および Audience Management を実装する準備は以上です。
