---
description: この情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: この情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。
seo-title: Analytics の概要
solution: Experience Cloud,Analytics
title: Analytics の概要
topic-fix: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
exl-id: ed9f55e6-f3ab-4c1e-9a2f-1ee67a7b4c03
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 100%

---

# Analytics の概要 {#analytics}

この節の情報は、Android SDK を Adobe Analytics で使用する場合に役立ちます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## Analytics トラッキング識別子の生成

SDK では、識別子を使用してユーザーを追跡します。識別子の階層は次のとおりです。

1. カスタム訪問者識別子（VID）
1. Analytics トラッキング識別子（AID）
1. Experience Cloud 識別子（MID）

>[!TIP]
>
>Experience Cloud 識別子の正しい頭字語は「ECID」です。SDK ではまだ、古い名称である「MID」を使用しています。

AID はトラッキング識別子とも呼ばれ、アプリが MID を使用するように設定されていない場合に SDK によって生成されます。その値は、起動からアプリのアップグレードまでの間、`SharedPreferences` で保持されます。ユーザーがデバイスからアプリを削除してから再インストールした場合、またはアプリ開発者が SharedPreferences をクリアした場合、SDK によって新しい識別子が生成されます。このプロセスにより、Analytics レポートに新しいユーザーが作成されます。

ID サービスのサポート（MID）を導入するアプリのユーザーの場合、既存の AID 値が Analytics のヒットと共に送信され、Analytics のヒットには AID と MID が含まれます。ID サービスがサポートされるアプリの新規ユーザーの場合、Analytics リクエストには MID のみが含まれます。訪問者の識別について詳しくは、「[訪問者の識別](https://docs.adobe.com/content/help/ja-JP/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-calculate.html)」を参照してください。
