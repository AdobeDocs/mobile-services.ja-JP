---
description: アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートします。
keywords: mobile
seo-description: アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートします。
seo-title: メッセージ
solution: Experience Cloud,Analytics
title: メッセージ
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 77%

---


# メッセージ {#messaging}

アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートできます。

## 新しい Adobe Experience Cloud SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* To get started, go to [Launch](https://launch.adobe.com/).
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> Adobe Experience Platform Mobile SDK を Adobe Launch で使用している場合、ダウンロード計測用リンクなどの機能を使用するには、Adobe Analytics Mobile Services 拡張機能もインストールする&#x200B;**必要があります**。詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。Experience Platform SDK でのプッシュメッセージおよびアプリ内メッセージの使用について詳しくは、「[プッシュメッセージのセットアップ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)」および「[アプリ内メッセージのセットアップ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)」を参照してください。

## アプリ内メッセージ{#section_8984F4568BC24D32A87429FFCB5184A6}

アプリ内メッセージは、ユーザーの行動と特徴に基づいて、リアルタイムに配信されます。メッセージの表示条件は、SDK によって既に計測されている Analytics データを組み合わせて指定できます。

次のメッセージタイプがサポートされています。

* カスタムおよびテーマ
* フルスクリーン
* ネイティブアラート
* ローカル通知

アプリ内メッセージのしくみを理解できるよう、追加情報を次に示します。

* アプリ内メッセージには SDK バージョン 4.2 以降が必要です。
* モバイルアプリ管理者権限を持つユーザーを指定する必要があります。

   これらの権限があれば、ダウンロード計測用リンクとアプリ内メッセージにアクセスできます。詳しくは、「[ロールと権限](/help/using/gs/c-mob-roles-and-permissions.md)」を参照してください。
* メッセージが承認されると、自動的にアプリに発行されます。
* 特徴、トリガー、スケジュールなどのメッセージパラメーターが満たされると、SDKがメッセージを表示します。
* メッセージには、カスタムHTMLや画像を含めることができます。オンラインURLを使用できます。

   オフライン時にトリガーされるメッセージに対しては、アプリバンドルのバックアップまたは代替イメージを指定することもできます。
* 表示されたメッセージは、合計表示回数、クリックスルー率などのレポートを提供します
* カスタムメッセージにテンプレートを使用できます。これにより、独自のアプリ内メッセージを簡単に作成できます。

## プッシュメッセージ {#section_90555A55BCE7427A90B1577E14BEF51B}

プッシュメッセージは、通知の受信を希望するユーザーに送信されます。これらのプッシュメッセージは、Analytics のセグメントまたはカスタムセグメントのユーザーに向けてターゲット設定できます。プッシュメッセージを使用すると、アプリを使用していない状態でも表示されるので、積極的にアプリを利用していないユーザーにアプリの利用を働きかけたり、特定の時間や場所に限定した情報を伝えることができます。

プッシュメッセージを設定する前に、「[プッシュメッセージを有効にするための前提条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)」を参照してください。これらのタスクを実行した後、アプリの設定でプッシュメッセージを設定する必要があります。 For more information, see [Configure push messaging](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
