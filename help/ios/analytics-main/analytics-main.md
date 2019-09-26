---
description: iOS SDK を Adobe Analytics で使用するのに役立つ情報です。
seo-description: iOS SDK を Adobe Analytics で使用するのに役立つ情報です。
seo-title: 解析の概要
solution: Marketing Cloud,Analytics
title: 解析の概要
topic: 開発者と導入
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# 解析の概要 {#analytics}

The information in this section helps you use the iOS SDK with Adobe Analytics.

## New Adobe Experience Platform Mobile SDK Release

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launchに移動します。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## Analytics追跡識別子の生成

SDK では、識別子を使用してユーザーをトラッキングします。以下に識別子の階層を示します。

1. カスタム訪問者識別子（VID）
2. Analytics トラッキング識別子（AID）
3. Experience Cloud 識別子（MID）

>[!TIP]
>
>Experience cloud識別子の正しい頭字語はECIDです。 SDK ではまだ MID を使用していますが、古い名称です。AID はトラッキング識別子とも呼ばれ、アプリが MID を使用するように設定されていない場合に SDK によって生成されます。その値は、起動からアプリのアップグレードまでの間、`NSUserDefaults` で保持されます。ユーザーがデバイスからアプリを削除してから再インストールした場合、またはアプリ開発者が `NSUserDefaults` をクリアした場合、SDK によって新しい識別子が生成されます。このプロセスにより、Analytics レポートに新しいユーザーが追加されます。

ID サービスサポート（MID）を導入するアプリのユーザーの場合、既存の AID 値は Analytics のヒットと共に送信され、Analytics のヒットには AID と MID が含まれます。ID サービスをサポートするアプリの新規ユーザーの場合、Analytics リクエストには MID のみが含まれます。For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
