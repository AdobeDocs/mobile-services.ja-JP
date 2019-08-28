---
description: iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションというエクステンションを作成できるようになりました。このエクステンションにはデータを共有する本体アプリがないので、アプリグループは必要ありません。
seo-description: iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションというエクステンションを作成できるようになりました。このエクステンションにはデータを共有する本体アプリがないので、アプリグループは必要ありません。
seo-title: スタンドアロンエクステンション実装
solution: Marketing Cloud、Analytics
title: スタンドアロンエクステンション実装
topic: 開発者と導入
uuid: 9b47f082- b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

iOS 10 以降、本体アプリなしで配布できる、スタンドアロンエクステンションというエクステンションを作成できるようになりました。このエクステンションにはデータを共有する本体アプリがないので、アプリグループは必要ありません。

>[!IMPORTANT]
>
>スタンドアロンの拡張機能を使用するには、モバイルSDKバージョン4.13.0以降が必要です。

## SDK でスタンドアロンエクステンションを使用するための設定 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

スタンドアロンエクステンションを設定するには：

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. 以下のライブラリおよびフレームワークをリンクします。

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. エクステンションのメインビューコントローラーで、SDK 関連のアクティビティを実行する前に、エクステンションタイプを SDK の `ADBMobileAppExtensionTypeStandAlone` に設定します。

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

追加情報を以下に示します。

* データの取得元が本体アプリかエクステンションかを示すためのコンテキストデータ値 `a.RunMode` が追加されました。

   * `a.RunMode = Application`

      この値は、ヒット元が本体アプリであることを意味します。
   * `a.RunMode = Extension`

      この値は、ヒット元がエクステンションであることを意味します。

* iOS エクステンションアプリに対してライフサイクルコールはトリガーされません。

