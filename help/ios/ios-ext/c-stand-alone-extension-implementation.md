---
description: iOS 10以降、Appleでは、スタンドアロン拡張機能と呼ばれる拡張機能を作成できます。この拡張機能は、iOS 10から、アプリケーションを含まないで配布できます。 この拡張機能を使用すると、データを共有するアプリは含まれないので、アプリグループは必要ありません。
seo-description: iOS 10以降、Appleでは、スタンドアロン拡張機能と呼ばれる拡張機能を作成できます。この拡張機能は、iOS 10から、アプリケーションを含まないで配布できます。 この拡張機能を使用すると、データを共有するアプリは含まれないので、アプリグループは必要ありません。
seo-title: スタンドアロンエクステンション実装
solution: Experience Cloud,Analytics
title: スタンドアロンエクステンション実装
topic: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 44%

---


# スタンドアロンエクステンション実装 {#stand-alone-extension-implementation}

iOS 10以降、Appleでは、スタンドアロン拡張機能と呼ばれる拡張機能を作成できます。この拡張機能は、iOS 10から、アプリケーションを含まないで配布できます。 この拡張機能を使用すると、データを共有するアプリは含まれないので、アプリグループは必要ありません。

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

      この値は、ヒットが拡張子から発生したことを意味します。

* iOS拡張機能アプリでは、ライフサイクル呼び出しはトリガーされません。

