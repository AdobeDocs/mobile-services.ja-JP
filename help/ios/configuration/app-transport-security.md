---
description: iOS 9 の一連の新しいセキュリティ要件である App Transport Security（ATS）への対応に役立つ情報です。
solution: Experience Cloud Services,Analytics
title: App Transport Security
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# App Transport Security {#app-transport-security}

iOS 9 の一連の新しいセキュリティ要件である App Transport Security（ATS）への対応に役立つ情報です。

Apple では、iOS 9 以降、セキュアな接続を実現するベストプラクティスに基づいて一連の要件を規定した App Transport Security が導入されました。詳しくは、「*Information Property List Key Reference（情報プロパティリストキーのリファレンス）*」/」の「[NSAppTransportSecurity](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)」を参照してください。

Adobe Mobile SDK バージョン 4.7 以降で ATS にシームレスに対応するためには、アプリ設定ページの SSL の有効化オプションを使用します。詳しくは、「[アプリ設定の管理](/help/using/c-manage-app-settings/c-manage-app-settings.md)」または「[ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)」を参照してください。

Adobe Mobile Servicesで、アプリ設定の&#x200B;**[!UICONTROL HTTPS を使用]**&#x200B;オプションを選択することで、Analytics、Audience Manager、Target および Adobe Experience Platform ID サービスからのすべてのヒットが HTTPS を使用して送信されるようになります。

別の方法として、次のサーバーを「許可リスト」に配置することもできます。

| 製品 | 説明 |
|--- |--- |
| Analytics | Analytics サーバーを許可するには、トラッキングサーバードメインを ATS 用の例外ドメインとして info.plist ファイルに追加します。トラッキングサーバードメインは、`ADBMobileConfig.json` ファイルの Analytics セクションまたはアプリ設定ページの Analytics セクションにあります。 |
| Audience Manager | Audience Manager ドメインは、`ADBMobileConfig.json` ファイルの audienceManager オブジェクトの server プロパティにあります。アプリ内で Audience Manager を使用しており、SSL が有効になっていない場合は、このサーバーを ATS 用の例外ドメインとして `Info.plist` ファイルに追加します。 |
| Target | Target エンドポイントを ATS 用の例外ドメインとして Info.plist ファイルに追加できます。Target エンドポイントを見つけるには、`clientCodeproperty` ファイルの target オブジェクト内にある `ADBMobileConfig.json` を探します。エンドポイントは `https://{clientCode}.tt.omtrdc.net` になります。例えば、`clientCodeproperty` が `"myCompany"` の場合、エンドポイントは `https://myCompany.tt.omtrdc.net` になります。 |
| Adobe Experience Platform ID サービス | ATS の例外ドメインとして、Experience Cloud サーバーを `Info.plist` ファイルに追加できます。このドメインは `dpm.demdex.net` です。 |
| Mobile Services：獲得 | `Info.plist` ファイルで、ATS の例外ドメインとして獲得サーバーをホワイトリストに許可します。このドメインは `c00.adobe.com` です。 |
| Mobile Services：アプリ内メッセージ | アプリ内メッセージを使用する場合は、HTTPS 以外の URL を使用するたびに、ATS の例外ドメインにエントリを追加する必要が出ることがあります。このリストには、ホスティングされている画像と、カスタムの全画面表示メッセージ HTML に埋め込まれている URL が含まれます。`info.plist` ファイル内の例外ドメインの設定の詳細については、*Table 2: App Transport Security dictionary primary keys（表 2：App Transport Security 辞書プライマリキー）* の *NSExceptionDomains* 行を参照してください。詳しくは、「*Information Property List Key Reference（情報プロパティリストキーのリファレンス）*」の「[Table 3 Exception domains dictionary keys（表 3 例外ドメイン辞書キー）](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)」を参照してください。 |

>[!TIP]
>
>これらの検討事項は、Adobe Mobile SDK が作成する接続に影響しますが、アプリが作成する Web ビューまたはその他の接続には影響しません。
