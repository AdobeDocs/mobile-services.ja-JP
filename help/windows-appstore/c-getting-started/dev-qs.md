---
description: 開発者向けクイックスタート記事
solution: Experience Cloud Services,Analytics
title: 開発者向けクイックスタート
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# 開発者向けクイックスタート {#developer-quick-start}

SDK を実装するには、Visual Studio 2013 以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

解凍後、 [SDK のダウンロード](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)を使用する場合、サポートされるアーキテクチャとプラットフォームの組み合わせごとに別々のフォルダーが用意されます。 また、 `ADBMobileConfig.json` ファイルに含める必要があります。

## 正しいバージョンを選択してください {#section_E53C5AA7D5474824A89BB32C003865A1}

異なる `.dll`/ `.winmd` ファイルは、各ターゲットプラットフォーム (Windows 8.1、Windows Phone 8.1) と、サポートされるアーキテクチャ (x86、x64、ARM) に対して提供されます。 ファイルは、次の手順に従ってフォルダー構造に分割されます。

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>のバージョン。 `ADBMobile.winmd` は、ライブラリのバージョンを反映していません。 この `.winmd` ファイルにはメタデータのみが含まれているので、ファイルのバージョン番号は `255.255.255.255` Microsoftで受け入れられる行動 ( [WinRT C++/CX コンポーネント dll のアセンブリ情報を追加する方法を教えてください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode) ）サードパーティリクエストを待機する、特別なコア Adobe JavaScript モジュールです。使用しているライブラリのバージョンを確認するには、基になるライブラリのバージョンを確認します `ADBMobile.dll` ファイル。

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 ユニバーサルApp Storeライブラリは、複数のプログラミング言語で使用できます。 このガイドの例は WinJS (JavaScript) にあり、別の言語を使用する場合は変更が必要になる場合があります。 winJS (JavaScript) から winmd メソッドを使用する場合、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。

また、WinJS プロジェクトで SDK を使用する場合は、空の文字列 ( `""` または `''`) の代わりに `null` 空の文字列値の場合。

## プロジェクトへのライブラリと設定ファイルの追加 — C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. 内 **ソリューションエクスプローラ**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイル。

   詳しくは、 *正しいバージョンを選択してください* 」の節を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 確認する `ADBMobile.winmd` が **[!UICONTROL 参照マネージャ]** ウィンドウとクリック **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Windows Phone アプリに参照を追加する場合は、 `ADBMobile.winmd`、デフォルトのファイルフィルターを次の場所から変更 **[!UICONTROL コンポーネントファイル]** から **すべてのファイル**.

1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

   ソリューションに C++プロジェクトも存在する場合は、この手順をスキップします。

1. 内 **Windows** タブをクリックし、「 **[!UICONTROL 拡張機能]**、を選択して、 **[!UICONTROL Windows 用Microsoft Visual C++ 2013 ランタイムパッケージ]**.

1. クラスに次の行を追加します。

   ```
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. を参照します。 `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. 変更 **[!UICONTROL アクションを作成]** から **[!UICONTROL コンテンツ]**.

## プロジェクトにライブラリと設定ファイルを追加します — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. 内 **[!UICONTROL ソリューションエクスプローラ]**、プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 参照]**.

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイル。

   詳しくは、 *正しいバージョンを選択* 」の節を参照してください。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 内 **[!UICONTROL 参照マネージャ]** ウィンドウ、確認します。 `ADBMobile.winmd` を選択し、 **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Windows Phone アプリに参照を追加する場合は、 `ADBMobile.winmd`、デフォルトのファイルフィルターを次の場所から変更 **[!UICONTROL コンポーネントファイル]** から **すべてのファイル**.

1. クラスに次の行を追加します。

   ```
   using namespace ADMS::Measurement;
   ```

1. プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. 次を参照： `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. の **[!UICONTROL 一般]** タブ、変更 **[!UICONTROL コンテンツ]** から **[!UICONTROL はい]**&#x200B;をクリックし、 **[!UICONTROL OK]**.

## プロジェクトへのライブラリと設定ファイルの追加 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。
1. 内 **ソリューションエクスプローラ**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

   詳しくは、 *正しいバージョンを選択* 」の節を参照してください。

1. ライブラリの正しいバージョンを選択し、関連する `ADBMobile.winmd` ファイル。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 確認する `ADBMobile.winmd` が **[!UICONTROL 参照マネージャ]** ウィンドウとクリック **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Windows Phone アプリに参照を追加する場合は、 `ADBMobile.winmd`、デフォルトのファイルフィルターを次の場所から変更 **[!UICONTROL コンポーネントファイル]** から **すべてのファイル**.

1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

   ソリューションに C++プロジェクトも存在する場合は、この手順をスキップします。

1. 内 **[!UICONTROL Windows]** タブをクリックし、「 **[!UICONTROL 拡張機能]** を選択して、 **[!UICONTROL Windows 用Microsoft Visual C++ 2013 ランタイムパッケージ]**.

1. プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. 次を参照： `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json]` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. を使用 **[!UICONTROL ファイルのプロパティ]** 選択済み、 **[!UICONTROL パッケージアクション]** が **[!UICONTROL コンテンツ]**.

   JavaScript プロジェクトの場合、ファイルはに設定されます。 **[!UICONTROL コンテンツ]** デフォルトでは。

## ADBMobileConfig.json 設定ファイルを更新します。 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

この `ADBMobileConfig.json` ファイルにはグローバル SDK 設定が含まれ、 *プロジェクトへのライブラリと設定ファイルの追加* 」セクションに入力します。 次に、 `ADBMobileConfig.json` ファイルがAdobeMobile Services によって事前設定されていなかった場合、まずいくつかの値を更新する必要があります。

次に、 `ADBMobileConfig.json` ファイル：

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

少なくとも、使用しているソリューションの次の値を更新します。

* **Analytics**: `rsids` および `server`
* **Target**: `clientCode`
* **Audience Management**: `server`

詳しくは、 [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK のデバッグを有効にするには、を呼び出す必要があります `ADBMobile.Config.setDebugLogging(true);`.

C Sharp および JS アプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります ( ネイティブコードのデバッグは C++アプリのデフォルト設定です )。

### C シャープ

プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL プロパティ]** > **[!UICONTROL 「デバッグ」タブ]**. 「デバッガー」ドロップダウンで、「 **[!UICONTROL ネイティブのみ]**.

### JS

プロジェクトを右クリックし、「 」を選択します。  **[!UICONTROL プロパティ]** > **[!UICONTROL 設定プロパティ]** > **[!UICONTROL 「デバッグ」タブ]**. デバッガータイプのドロップダウンを「 **ネイティブのみ**.

これで作業は完了です。これで、Windows 8.1 Universal App Storeアプリに Analytics、Target および Audience Management を実装する準備が整いました。
