---
description: この情報は、Adobe AnalyticsでiOS SDKを使用する際に役立ちます。
seo-description: この情報は、Adobe AnalyticsでiOS SDKを使用する際に役立ちます。
seo-title: Analytics の概要
solution: Experience Cloud,Analytics
title: Analytics の概要
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 67%

---


# Analytics の概要 {#analytics}

この節の情報は、iOS SDK を Adobe Analytics で使用する場合に役立ちます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## Analytics トラッキング識別子の生成

SDKでは、識別子を使用してユーザーを追跡します。識別子は次の階層にあります。

1. カスタム訪問者識別子(VID)
1. Analytics追跡識別子(AID)
1. Experience Cloud識別子(MID)

>[!TIP]
>
>Experience Cloud 識別子の正しい頭字語は ECID です。SDK ではまだ MID を使用していますが、古い名称です。

AID はトラッキング識別子とも呼ばれ、アプリが MID を使用するように設定されていない場合に SDK によって生成されます。その値は、起動からアプリのアップグレードまでの間、`NSUserDefaults` で保持されます。ユーザーがデバイスからアプリを削除してから再インストールした場合、またはアプリ開発者が `NSUserDefaults` をクリアした場合、SDK によって新しい識別子が生成されます。このプロセスにより、Analyticsレポートに新しいユーザーが作成されます。

IDサービスのサポート(MID)を導入するアプリのユーザーの場合、既存のAID値がAnalyticsのヒットと共に送信され、AnalyticsのヒットにAIDとMIDが含まれます。 IDサービスがサポートされるアプリの新規ユーザーの場合、AnalyticsリクエストにはMIDのみが含まれます。 訪問者の識別について詳しくは、「[訪問者の識別](https://docs.adobe.com/content/help/ja-JP/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)」を参照してください。
