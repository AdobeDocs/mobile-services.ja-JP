---
description: この情報は、iOS SDK を Adobe Analytics で使用する場合に役立ちます。
solution: Experience Cloud Services,Analytics
title: Analytics の概要
topic-fix: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
exl-id: 7c383b1d-2e59-4473-9de5-80c84d896f6d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 95%

---

# Analytics の概要 {#analytics}

この節の情報は、iOS SDK を Adobe Analytics で使用する場合に役立ちます。

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

AID はトラッキング識別子とも呼ばれ、アプリが MID を使用するように設定されていない場合に SDK によって生成されます。その値は、起動からアプリのアップグレードまでの間、`NSUserDefaults` で保持されます。ユーザーがデバイスからアプリを削除してから再インストールした場合、またはアプリ開発者が `NSUserDefaults` をクリアした場合、SDK によって新しい識別子が生成されます。このプロセスにより、Analytics レポートに新しいユーザーが作成されます。

ID サービスのサポート（MID）を導入するアプリのユーザーの場合、既存の AID 値が Analytics のヒットと共に送信され、Analytics のヒットには AID と MID が含まれます。ID サービスがサポートされるアプリの新規ユーザーの場合、Analytics リクエストには MID のみが含まれます。訪問者の識別について詳しくは、 [実訪問者数](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=ja) (Adobe Analyticsドキュメント ) を参照してください。
