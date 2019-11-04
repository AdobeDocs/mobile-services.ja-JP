---
description: この情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: この情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。
seo-title: Analytics の概要
solution: Experience Cloud,Analytics
title: Analytics の概要
topic: 開発者と導入
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Analytics の概要 {#analytics}

この節の情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## Analytics トラッキング識別子の生成

SDK では、識別子を使用してユーザーをトラッキングします。以下に識別子の階層を示します。

1. カスタム訪問者識別子（VID）
2. Analytics トラッキング識別子（AID）
3. Experience Cloud 識別子（MID）

>[!TIP]
>
>Experience Cloud 識別子の正しい頭字語は ECID です。SDK ではまだ MID を使用していますが、古い名称です。

AID はトラッキング識別子とも呼ばれ、アプリが MID を使用するように設定されていない場合に SDK によって生成されます。その値は、起動からアプリのアップグレードまでの間、`SharedPreferences` で保持されます。ユーザーがデバイスからアプリを削除してから再インストールした場合、またはアプリ開発者が SharedPreferences をクリアした場合、SDK によって新しい識別子が生成されます。このプロセスにより、Analytics レポートに新しいユーザーが追加されます。

ID サービスサポート（MID）を導入するアプリのユーザーの場合、既存の AID 値は Analytics のヒットと共に送信され、Analytics のヒットには AID と MID が含まれます。ID サービスをサポートするアプリの新規ユーザーの場合、Analytics リクエストには MID のみが含まれます。訪問者の識別について詳しくは、「[訪問者の識別](https://docs.adobe.com/content/help/ja-JP/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)」を参照してください。