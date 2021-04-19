---
description: Apple では iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションと呼ばれる拡張機能を作成できます。この拡張機能にはデータを共有する本体アプリがないので、アプリグループは必要ありません。
seo-description: Apple では iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションと呼ばれる拡張機能を作成できます。この拡張機能にはデータを共有する本体アプリがないので、アプリグループは必要ありません。
seo-title: スタンドアロンエクステンション実装
solution: Experience Cloud,Analytics
title: スタンドアロンエクステンション実装
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---

# スタンドアロンエクステンション実装 {#stand-alone-extension-implementation}

Apple では iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションと呼ばれる拡張機能を作成できます。この拡張機能にはデータを共有する本体アプリがないので、アプリグループは必要ありません。

>[!IMPORTANT]
>
>スタンドアロンエクステンションを使用するには、Mobile SDK バージョン 4.13.0 以降が必要です。

## SDK でスタンドアロンエクステンションを使用するための設定 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

スタンドアロンエクステンションを設定するには：

1. `ADBMobileConfig.json` ファイルがエクステンションのターゲットのメンバーであることを確認します。
1. 以下のライブラリおよびフレームワークをリンクします。

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. エクステンションのメインビューコントローラーで、SDK 関連のアクティビティを実行する前に、エクステンションタイプを SDK の `ADBMobileAppExtensionTypeStandAlone` に設定します。

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

## 追加情報 {#section_1C9A55E2309A44BF842310F735702B3D}

追加情報を以下に示します。

* データの取得元が本体アプリかエクステンションかを示すためのコンテキストデータ値 `a.RunMode` が追加されました。

   * `a.RunMode = Application`

      この値は、ヒット元が本体アプリであることを意味します。
   * `a.RunMode = Extension`

      この値は、ヒット元が拡張機能であることを示します。

* iOS 拡張アプリに対しては、ライフサイクルコールはトリガーされません。
