---
description: iOS 9 の一連の新しいセキュリティ要件である App Transport Security（ATS）への対応に役立つ情報です。
seo-description: iOS 9 の一連の新しいセキュリティ要件である App Transport Security（ATS）への対応に役立つ情報です。
seo-title: App Transport Security
solution: Marketing Cloud、Analytics
title: App Transport Security
topic: 開発者と導入
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

iOS 9 の一連の新しいセキュリティ要件である App Transport Security（ATS）への対応に役立つ情報です。

Apple では、iOS 9 以降、セキュアな接続を実現するベストプラクティスに基づいて一連の要件を規定した App Transport Security が導入されました。詳しくは、"Information *Property List Key Reference* 」の [NSAppTransportSecurity](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)を参照してください。

Adobe Mobile SDK バージョン 4.7 以降で ATS にシームレスに対応するためには、アプリ設定ページの SSL の有効化オプションを使用します。詳しくは、アプリ設定 [](/help/using/c-manage-app-settings/c-manage-app-settings.md) または [ADBMobile JSON設定を参照](/help/ios/configuration/json-config/json-config.md)してください。

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

代わりに、次のサーバーをホワイトリストに登録できます。

| 製品 | 説明 |
|--- |--- |
| Analytics | Analytics サーバーをホワイトリストに登録するには、トラッキングサーバードメインを ATS 用の例外ドメインとして info.plist ファイルに追加します。トラッキングサーバードメインは、`ADBMobileConfig.json` ファイルの Analytics セクションまたはアプリ設定ページの Analytics セクションにあります。 |
| Audience Manager | Audience Manager ドメインは、`ADBMobileConfig.json` ファイルの audienceManager オブジェクトの server プロパティにあります。アプリ内で Audience Manager を使用しており、SSL が有効になっていない場合は、このサーバーを ATS 用の例外ドメインとして `Info.plist` ファイルに追加します。 |
| Target  | Target エンドポイントを ATS 用の例外ドメインとして Info.plist ファイルに追加できます。Target エンドポイントを見つけるには、`clientCodeproperty` ファイルの target オブジェクト内にある `ADBMobileConfig.json` を探します。Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform IDサービス | ATS の例外ドメインとして、Experience Cloud サーバーを `Info.plist` ファイルに追加できます。This domain is `dpm.demdex.net`. |
| Mobile Services：獲得 | `Info.plist` ファイルで、ATS の例外ドメインとして獲得サーバーをホワイトリストに登録します。This domain is `c00.adobe.com`. |
| Mobile Services：アプリ内メッセージ | アプリ内メッセージを使用している場合、使用している HTTPS 以外の URL ごとに、ATS の例外ドメインにエントリを追加する必要がある場合があります。このリストには、ホスティングされている画像と、カスタムの全画面表示メッセージ HTML に埋め込まれている URL が含まれます。`info.plist` ファイル内の例外ドメインの設定について詳しくは、表2の *NSDExceptionDomains* 行を参照 *してください。App Transport Security辞書のプライマリキー*。"Information *Property List Key Reference* »の?«Table3Exception Domains[](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/) |

>[!TIP]
>
>これらの考慮事項は、Adobe Mobile SDKが行った接続に影響し、アプリケーションによって行われるWebビューやその他の接続には影響しません。

