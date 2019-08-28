---
description: アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートします。
keywords: モバイル
seo-description: アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートします。
seo-title: メッセージ
solution: Marketing Cloud、Analytics
title: メッセージ
topic: 指標
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# メッセージ {#messaging}

アプリ内メッセージおよびプッシュメッセージを作成、管理およびレポートできます。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、[Launch](https://launch.adobe.com/) にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。Experience Platform SDK でのプッシュメッセージおよびアプリ内メッセージの使用について詳しくは、「[プッシュメッセージのセットアップ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)」および「[アプリ内メッセージのセットアップ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)」を参照してください。

## In-app messages {#section_8984F4568BC24D32A87429FFCB5184A6}

アプリ内メッセージは、ユーザーの行動と特徴に基づいて、リアルタイムに配信されます。メッセージの表示条件は、SDK によって既に計測されている Analytics データを組み合わせて指定できます。

次のメッセージタイプがサポートされています。

* カスタムおよびテーマ
* フルスクリーン
* ネイティブアラート
* ローカル通知

アプリ内メッセージの機能を理解するために、以下の点について説明します。

* アプリ内メッセージにはSDKバージョン4.2以降が必要です。
* モバイルアプリ管理者権限を持つユーザーを指定する必要があります。

   これらの権限により、ダウンロード計測用リンクおよびアプリ内メッセージにアクセスできます。詳しくは [、ロールと権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。
* メッセージが承認されると、自動的にアプリに発行されます。
* メッセージパラメーター（traits、trigger、schedule など）の条件が一致すると、メッセージが表示されます。
* メッセージは、リモートの HTML や画像を URL で指定できます。

   メッセージがオフライン時に表示された場合の対策として、アプリバンドル内に保存する代替イメージも指定できます。
* 表示されたメッセージは、合計表示回数、クリックスルー率などのレポートを提供します
* カスタムメッセージにテンプレートを使用できます。これにより、独自のアプリ内メッセージを簡単に作成できます。

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

プッシュメッセージは、通知の受信を希望するユーザーに送信されます。これらのプッシュメッセージは、Analytics のセグメントまたはカスタムセグメントのユーザーに向けてターゲット設定できます。プッシュメッセージを使用すると、アプリを使用していない状態でも表示されるので、積極的にアプリを利用していないユーザーにアプリの利用を働きかけたり、特定の時間や場所に限定した情報を伝えることができます。

プッシュメッセージを設定する前に、プッシュメッセージを有効にする [ための前提条件を参照](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)してください。これらのタスクを実行した後、アプリの設定でプッシュメッセージを設定する必要があります。詳しくは、[プッシュメッセージ](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md)を設定します。