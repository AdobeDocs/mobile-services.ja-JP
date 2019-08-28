---
description: Adobe Mobile Services のよくある質問と回答、および一般的な機能説明です。
keywords: モバイル
seo-description: Adobe Mobile Services のよくある質問と回答、および一般的な機能説明です。
seo-title: よくある質問
solution: Marketing Cloud、Analytics
title: よくある質問
topic: 指標
uuid: 62a9241c-2ada-483a- a594- b023916cb0b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# よくある質問 {#frequently-asked-questions}

次の表に、Adobe Mobile Servicesに関するよくある質問の一覧を示します。

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### SDK は頻繁に更新されますか？

はい、最も機能が豊富で、標準に準拠し、安全な SDK を提供するために、更新は常におこなっています。通常、毎月新しいバージョンをリリースします。これらの SDK のアップデートは、容易な実装を支援するための当座の代替（バージョン4x 向け）です。アップデートについて詳しくは、[リリースノート](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)を参照してください。

### どの SDK バージョンを使用すべきですか？

現在の SDK は、バージョン 4.11 です。詳しくは、[リリースノート](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html)を参照してください。

### SDK はどこからダウンロードできますか？

個々のモバイルプラットフォームのSDKは、「アプリ設定 [を管理」](/help/using/c-manage-app-settings/c-manage-app-settings.md) セクションに移動してダウンロードできます。

### SDK の設定方法を教えてください。

新しいアプリレポートスイートを作成したら、「アプリ設定を管理」に移動し、アプリの情報ページで必要なすべてのオプションを設定します。設定を保存したら、アプリ設定ページ下部から必要な SDK をダウンロードします。The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Adobe Mobile SDK は、iOS の IPv6 をサポートしますか？

Adobe Mobile SDK は、標準的な iOS および Android ネットワークスタックを使用します。iOSの場合、SDKはIPv6に完全に準拠しているNSURLSession（iOSバージョン7以降）およびNSURLConnection（iOSバージョン7以降）を使用します。独自のネットワークスタックを構築または使用した開発者は、その他の緩和の考慮事項があるかどうかを確認できます。Appleからの追加情報を次に示します。

*NSURLSessionやCFNetworkフレームワークなどの高レベルのネットワーキングAPIを使用してクライアントサイドのアプリケーションを記述し、名前で接続する場合、IPv6アドレスを使用するためにアプリケーションを変更する必要はありません。* 詳しくは、 [IPv6DNS64/NAT64ネットワークをサポート](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)しています。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### ライフサイクル指標とは何ですか？

ライフサイクル指標は、SDK が最初にアプリに実装される際に自動的に収集される、「そのまま使用できる」指標です。詳しくは [、ライフサイクル指標（Android）](/help/android/metrics.md) および [ライフサイクル指標（iOS）](/help/ios/metrics.md)を参照してください。

### 処理ルールをトラブルシューティングする方法を教えてください。

詳しくは、[処理ルールのヒントとテクニック](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)を参照してください。

### 分析データを複数のレポートスイートに送信できますか？

はい。SDK は、複数の Adobe Analytics レポートスイートにデータを送信する機能を提供します。1 つのイメージリクエストを使用して複数のレポートスイートにデータを取り込むには、 ファイルの「**[!UICONTROL analytics]」セクションにある「****rsids[!UICONTROL 」フィールドに複数のレポートスイート ID を設定します（コンマ区切りで間にスペースを挟まない）。]**`ADBMobileConfig.json`詳しくは [、ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)を参照してください。

### Mobile の訪問者数は起動回数とどのように異なりますか？

起動は、ユーザーが最初にアプリを開いた際、または指定したタイムアウト値より長くアプリから離れた後で戻ってくる際に、SDK によって測定されます。The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. 訪問は、Adobe Analytics のサーバー側の計算で、訪問のタイムアウトに達する前に SDK によって送信された最初と最後のデータヒットに基づいています。通常、レポートスイートのセッションタイムアウトは 30 分です。訪問回数は、従来の Web 分析から来ていますが、これらのヒットは、ユーザーがどのようにアプリに出入りするかについて、依然として価値あるインサイトを提供します。

## メッセージ {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### プッシュ通知にはサイズまたはその他の制限はありますか？

プッシュ通知メッセージには、140 文字の制限があります。送信またはスケジュールできる通知の数、または送信される通知の頻度には、制限はありません。

### プッシュ通知のカスタムペイロードをサポートしますか？

はい、JSON でコード化できるカスタムプッシュペイロードを提供しています。Android および iOS ペイロードは、それぞれ 4 KB および 2 KB の制限があります。これらのペイロードは、プッシュまたはローカル通知を通じてアプリに送信されます。詳しくは [、エクスペリエンス:プッシュメッセージ](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)を参照してください。

### アプリ内メッセージにはサイズ制限はありますか？

Adobe Mobile Services で作成された、公開されたアクティブなアプリ内メッセージは、レポートスイートあたり 15 MB のサイズ制限でサーバーでホストされます。この制限が Adobe でホストするメッセージコンテンツおよびリソースに適用される間、他のホストまたはアプリ内でアプリ内メッセージがどのリソースを参照するかについて制限はありません。

### アプリ内メッセージで独自の HTML を使用できますか？

はい、アプリ内メッセージでのカスタム HTML をサポートしています。For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### プッシュ通知またはアプリ内メッセージの送信にどのようなトリガーを使用できますか？

マーケターは、アプリ内メッセージを表示するためのトリガーとして送信された任意の Analytics データまたはイベントを選択できます。アプリ内メッセージは、デバイス上でローカルに発生するトリガーを使用します。複数のトリガーを選択する場合、すべてのトリガーは、メッセージを表示するために、同じヒットで発生する必要があります。詳しくは、[エクスペリエンス：アプリ内メッセージ](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)を参照してください。

プッシュメッセージは、以前から存在する Adobe Analytics セグメントまたは既に収集された Analytics 履歴データを基に作成されたカスタムセグメントを使用して送信されます。詳しくは、 [エクスペリエンス：プッシュメッセージ](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### アプリ内、プッシュ、またはマーケティングリンク名に入力したのはなぜですか。

同じ親レポートスイートまたは VRS を使用する複数のアプリで、同じアプリ内メッセージ、プッシュメッセージまたはマーケティングリンク名を使用することはできません。この問題を解決するには、アプリ内メッセージ、プッシュメッセージまたはマーケティングリンクに別の名前を入力してください。

## ロケーション {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 持つことのできる目標（POI）の数に制限はありますか?

特別な制限はありませんが、理想的なパフォーマンスおよびユーザーのデバイスのメモリ制限のために、POI を作成または更新するのは、最大で 5,000 までにすることをお勧めします。

## 獲得 {#section_B37F1129CD5843E890D0E54179455357}

### アプリ内アクティビティにキャンペーンをアトリビュートできますか？

はい。Adobe Mobile Services は、アプリをプロモーションし、アクセスを促進して、獲得キャンペーンをアプリ内分析およびコンバージョンに結び付けるのに役立つ、マーケティングのテクニックを構築する支援をします。詳しくは、 [獲得](/help/using/acquisition-main/acquisition-main.md).

### 新しいアプリユーザーを獲得しトラッキングするためのリンクを設定するにはどうしたらよいですか？

Apple App StoreおよびGoogle Playからアプリをダウンロードするためのマーケティングリンクを作成できます。これらのリンクを使用すると、単なるダウンロード回数に加えて、このリンク経由でアプリをダウンロードした後のユーザー行動（ライフサイクル系指標や成功イベント）を長期で追えるようになります。詳しくは、 [マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).