---
title: AdobeMobile Services の提供終了に関する FAQ
description: AdobeMobile Services の提供終了のお知らせに関するよくある質問への回答を紹介します。
exl-id: c5f44341-7b87-4530-b86e-17e2911a7959
source-git-commit: c349c0f83df9d42b61a419ae71d6d2b67c5f7819
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# AdobeMobile Services の提供終了に関する FAQ

AdobeMobile Service の提供終了日： **2022 年 12 月 31 日**.

## 何が起こってるの？

Mobile Services が 2022 年 12 月 31 日 (PT) に提供終了となります。 モバイル中心の UI、獲得、ディープリンク、アプリ内メッセージ、プッシュ通知および位置情報をサポートする Mobile Services は、この日以降はサポートされなくなります。

## 何が含まれ、何が含まれないのか。

この提供終了には、スタンドアロンのAdobeである Mobile Services のみが含まれます。 [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). このインターフェイスに依存する Mobile バージョン 4 SDK は、2021 年 8 月 31 日に廃止されました。

この提供終了には、Adobe Experience Platform Mobile SDK の一部であるモバイルアプリ用のAdobe Analyticsは含まれません。 これらの機能（アプリ内動作、ライフサイクル分析、メッセージングインタラクショントラッキング、オーディエンスプロファイルなど）は、引き続きAdobeからサポートを受けます。

## 機能が廃止される理由

Adobeがモバイルマーケティング機能を拡大し続けるにつれ、以前 Mobile Services で使用できた機能は、Adobe Experience Cloudソリューションでリリースされるか、AdobeExchange プレミアパートナーを通じて提供されます。 この切り替えにより、より強力で柔軟なモバイルマーケティング機能が提供されます。

## Mobile Services で作成された既存の処理ルールはどうなりますか？

[処理ルール](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) Mobile Services UI で作成または生成されたデータは、Mobile Services の提供終了日の前に自動的にAdobe Analyticsに移行されます。 移行された処理ルールは、Adobe Analyticsの他の処理ルールと同様に動作します。処理ルールは自由に表示または編集できます。 この移行にユーザー操作は必要ありません。

Mobile Services の終了後、すべての処理ルールロジックは、通常、の使用を含め、Adobe Analytics内でのみ処理されます。 [コンテキストデータ変数](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=ja).

## 使用可能な切り替えオプションは何ですか？

Adobeでは、組織の使用例に応じて、3 つのトランジションパスを提供します。

1. **アプリ内メッセージおよびプッシュ通知**:Adobeは、メッセージングワークフローをAdobe Journey Optimizerに移行できます。 この製品を使用すると、モバイルメッセージを含め、カスタマージャーニー全体にわたって、組織がエクスペリエンスを最適化およびパーソナライズするのに役立ちます。
1. **獲得とディープリンク**:獲得とディープリンクは、Exchange Premier Partners プログラムを通じてAdobeで提供されます。 Adobeのパートナーシップチームは、お客様のニーズに最適なソリューションを確実に見つけるために、適切な紹介を行うことができます。
1. **Places Service**:Places Service は無料の位置情報機能を提供します。 詳しくは、 [Places Service ドキュメント](https://experienceleague.adobe.com/docs/places/using/home.html).

## 質問がある場合は、どこに移動できますか？

詳しくは、 [AdobeMobile Services の提供終了の Spark ページ](https://spark.adobe.com/page/C6D30y09zaRpD/) を参照してください。 その他のご質問については、Adobe担当者にお問い合わせください。
