---
description: ユニバーサル Windows プラットフォームライブラリの実装方法に関する情報です。
solution: Experience Cloud Services,Analytics
title: 開発者向けクイックスタート
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# 開発者向けクイックスタート{#developer-quick-start}

ユニバーサル Windows プラットフォームライブラリの実装方法に関する情報を以下に示します。

>[!IMPORTANT]
>
>SDK を実装するには、Visual Studio 2013 以降が必要です。

## SDK の取得 {#section_99FE1A17A36D4A2C943939023CF6265C}

解凍後、 [SDK のダウンロード](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) ファイルに保存すると、サポートされるアーキテクチャとプラットフォームの組み合わせごとに別のフォルダーが作成されます。 また、 `ADBMobileConfig.json` ファイル。 このファイルの詳細については、 [ADBMobileConfig.json 設定ファイル](/help/universal-windows/c-configuration/c.json.md).

## 正しいバージョンを選択してください {#section_E53C5AA7D5474824A89BB32C003865A1}

異なる `.dll/.winmd` ファイルは、サポートされるアーキテクチャ (x86、x64、ARM) ごとに提供されます。

>[!IMPORTANT]
>
>のバージョン。 `ADBMobile.winmd` は、ライブラリのバージョンを反映していません。 この `.winmd` ファイルにメタデータのみが含まれ、バージョン番号が `255.255.255.255`:Microsoftに従って受け入れられる動作です。 詳しくは、 [WinRT C++/CX コンポーネント dll のアセンブリ情報を追加する方法を教えてください。](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)に対する質問に回答します。使用しているライブラリのバージョンを確認するには、基になるライブラリのバージョンを確認します `ADBMobile.dll` ファイル。

## 構文の違い {#section_A02DE120B6D240F5AFFE7509755C4F14}

Universal Windows Platform ライブラリは、複数のプログラミング言語で使用できます。 このガイドの例は、WinJS (JavaScript) に記載されています。異なる言語を使用する場合は、変更が必要になる場合があります。 winJS の winmd メソッドを使用する場合、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

実装間の主な違いは、コンテキストデータに使用されるデータ構造です。 また、WinJS プロジェクトで SDK を使用する場合は、空の文字列 ( `""` または `''`) の代わりに `null` 空の文字列値の場合。

## プロジェクトへのライブラリと設定ファイルの追加 — C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Visual Studio を起動し、ソリューションを開きます。
1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

1. ライブラリの正しいバージョンを選択し、関連する ADBMobile.winmd ファイルを参照します。

   詳しくは、 *正しいバージョンを選択してください* 」セクションに表示されます。

1. 「**追加**」をクリックします。

1. ADBMobile.winmd ファイルが **[!UICONTROL 参照マネージャ]** ウィンドウとクリック **[!UICONTROL OK]**.

1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

   ソリューションに C++プロジェクトも含まれている場合は、この手順をスキップしてください。

1. 内 **[!UICONTROL Windows]** タブをクリックし、「 **[!UICONTROL 拡張機能]**、を選択して、 **[!UICONTROL ユニバーサル Windows プラットフォームアプリ用 Visual C++ 2015 Runtime]**.

1. クラスに次の行を追加します。

   ```csharp
   using ADBMobile;
   ```

1. プロジェクトを右クリックし、 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. 次を参照： `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. 変更 **[!UICONTROL アクションを作成]** から **[!UICONTROL コンテンツ]**.

## プロジェクトにライブラリと設定ファイルを追加します — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Visual Studio を起動し、ソリューションを開きます。
1. 内 **[!UICONTROL ソリューションエクスプローラ]**、プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 参照]**.

1. ライブラリの正しいバージョンを選択し、関連する ADBMobile.winmd ファイルへの参照を追加します。

   詳しくは、 *正しいバージョンを選択してください* 」セクションに表示されます。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. 確認する `ADBMobile.winmd` が **[!UICONTROL 参照マネージャ]** ウィンドウとクリック **[!UICONTROL OK]**.

1. クラスに次の行を追加します。

   ```c++
   using namespace ADBMobile;
   ```

1. プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. 参照先 `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. の **[!UICONTROL 一般]** タブ、変更 **[!UICONTROL コンテンツ]** から **[!UICONTROL はい]** をクリックし、 **[!UICONTROL OK]**.

## プロジェクトへのライブラリと設定ファイルの追加 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Visual Studio を起動し、ソリューションを開きます。

1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

1. ライブラリの正しいバージョンを選択し、関連する ADBMobile.winmd ファイルを参照します。

1. 「**[!UICONTROL 追加]**」をクリックします。

1. ADBMobile.winmd ファイルが **[!UICONTROL 参照マネージャ]** ウィンドウとクリック **[!UICONTROL OK]**.

1. 内 **[!UICONTROL ソリューションエクスプローラ]**、右クリック **[!UICONTROL 参照]** を選択し、 **[!UICONTROL 参照を追加]**.

   ソリューションに C++プロジェクトも含まれている場合は、この手順をスキップしてください。

1. 内 **[!UICONTROL Windows]** タブをクリックし、「 **[!UICONTROL 拡張機能]** を選択して、 **[!UICONTROL ユニバーサル Windows プラットフォームアプリ用 Visual C++ 2015 Runtime]**.

1. プロジェクトを右クリックし、「 」を選択します。 **[!UICONTROL 追加]** > **[!UICONTROL 既存の項目]**.

1. 次を参照： `ADBMobileConfig.json` ファイルを開き、 **[!UICONTROL 追加]**.

1. を右クリックします。 `ADBMobileConfig.json` ファイルを選択し、 **[!UICONTROL プロパティ]**.

1. を使用 **[!UICONTROL ファイルのプロパティ]** 選択済み、 **[!UICONTROL パッケージアクション]** が **[!UICONTROL コンテンツ]**.

   JavaScript プロジェクトの場合、ファイルはデフォルトで「コンテンツ」に設定されています。

## ADBMobileConfig.json 設定ファイルの更新 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

この `ADBMobileConfig.json` ファイルにはグローバル SDK 設定が含まれ、 *プロジェクトへのライブラリと設定ファイルの追加* 」セクションに入力します。 次に、 `ADBMobileConfig.json` ファイルがAdobeMobile Services によって事前設定されていなかった場合、まずいくつかの値を更新する必要があります。

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

少なくとも、使用しているソリューションの次の値を更新します。

* **Adobe Analytics**: `rsids` および `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

詳しくは、 [SDK メソッド](/help/universal-windows/c-configuration/methods.md).

## デバッグ {#section_3A10376A60394A15BEE483323E0CD4AA}

SDK のデバッグを有効にするには、を呼び出します。 `ADBMobile.Config.setDebugLogging(true);`.

C Sharp および JavaScript アプリの場合、次の手順を実行してネイティブコードのデバッグを有効にする必要があります ( ネイティブコードのデバッグは C++アプリのデフォルト設定です )。

### C シャープ

1. プロジェクトを右クリックし、  **[!UICONTROL プロパティ]** > **[!UICONTROL 「デバッグ」タブ]**.

1. デバッガータイプのドロップダウンを「 **ネイティブのみ**.

### JavaScript

1. プロジェクトを右クリックし、 **[!UICONTROL プロパティ]** > **[!UICONTROL 設定プロパティ]** > **[!UICONTROL 「デバッグ」タブ]**.

1. デバッガータイプのドロップダウンを「 **[!UICONTROL ネイティブのみ]**.

これで作業は完了です。これで、Universal Windows Platform アプリに Analytics、Target および Audience Management を実装する準備が整いました。
