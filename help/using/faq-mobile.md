---
description: Adobe Mobile Services のよくある質問と回答、および一般的な機能説明です。
keywords: mobile
seo-description: Adobe Mobile Services のよくある質問と回答、および一般的な機能説明です。
seo-title: よくある質問
solution: Experience Cloud,Analytics
title: よくある質問
topic: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '1118'
ht-degree: 100%

---


# よくある質問 {#frequently-asked-questions}

次の表に、Adobe Mobile Services に関するよくある質問の一覧を示します。

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### SDK は頻繁に更新されますか？

はい。最も機能が豊富で、標準に準拠し、安全な SDK を提供するために、継続的にアップデートを実施しています。通常は、毎月新しいバージョンをリリースします。これらの SDK アップデートは、容易に実装できるよう支援する、ドロップインの代替機能（バージョン 4x 向け）です。アップデートの詳細については、[リリースノート](https://docs.adobe.com/content/help/ja-JP/release-notes/experience-cloud/current.html)を参照してください。

### どの SDK バージョンを使用すべきですか？

現在の SDK は、バージョン 4.11 です。詳しくは、[リリースノート](https://docs.adobe.com/content/help/ja-JP/release-notes/experience-cloud/current.html)を参照してください。

### SDK はどこからダウンロードできますか？

個々のモバイルプラットフォーム向けの SDK は、「[アプリ設定](/help/using/c-manage-app-settings/c-manage-app-settings.md)」セクションにアクセスすることでダウンロードできます。

### SDK の設定方法を教えてください。

新しいアプリのレポートスイートを作成したら、アプリ設定に移動して、アプリの情報ページで必要なすべてのオプションを設定します。設定を保存したら、アプリ設定ページ下部から必要な SDK をダウンロードします。SDK は、保存したオプションで事前設定され、SDK パッケージ内の `ADBMobileConfig.json` ファイルにあります。アプリ設定ページの SDK 設定を変更する場合、SDK ファイルを再ダウンロードするか、`ADBMobileConfig.json` ファイルに必要な変更を加えて更新します。

### Adobe Mobile SDK は IPv6 for iOS をサポートしていますか。

Adobe Mobile SDK は、標準 iOS および Android ネットワークスタックを使用します。iOS の場合、SDK は、IPv6 に完全に準拠している NSURLSession（iOS バージョン 7 以降）および NSURLConnection（iOS バージョン 7 以降）を使用します。独自のネットワークスタックをビルドしたまたは使用する開発者は、その他の以降の考慮事項がないかどうかを確認してください。Apple の追加情報を次に示します。

*NSURLSession および CFNetwork フレームワークなどのハイレベルネットワーキング API を使用してクライアント側アプリを記述している場合で、名前で接続する場合、IPv6 アドレスで機能させるためにアプリを変更する必要はありません。* 詳細については、「[IPv6 DNS64／NAT64 ネットワークのサポート](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)」を参照してください。


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### ライフサイクル指標とは

ライフサイクル指標は、SDK が最初にアプリに実装されたときに自動的に収集される、「あらかじめ用意された」指標です。詳しくは、「[ライフサイクル指標（Android）](/help/android/metrics.md)」および「[ライフサイクル指標（iOS）](/help/ios/metrics.md)」を参照してください。

### 処理ルールをトラブルシューティングする方法を教えてください。

詳しくは、「[処理ルールのヒントとテクニック](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html)」を参照してください。

### 解析データを複数のレポートスイートに送信することはできますか。

はい。SDK は、複数の Adobe Analytics レポートスイートにデータを送信する機能を提供します。1 つのイメージリクエストを使用して複数のレポートスイートにデータを取り込むには、 フ `ADBMobileConfig.json` ァイルの  **[!UICONTROL analytics]** セクションにある **[!UICONTROL rsids]** フィールドに複数のレポートスイート ID を設定します（コンマ区切り、間にスペースを挟まない）。詳しくは、「[ADBMobile JSON の設定](/help/ios/configuration/json-config/json-config.md)」を参照してください。

### Mobile の訪問回数と起動回数の違いは何ですか？

起動は、ユーザーが最初にアプリを開いたとき、または指定したタイムアウト値より長くアプリを離れた後でアプリに戻ったときに、SDK によって測定されます。通常のタイムアウトは、 `ADBMobileConfig.json` ファイルの **[!UICONTROL lifecycleTimeout]** フィールドでは、5 分（300 秒）です。訪問は、Adobe Analytics によるサーバー側の計算で、訪問のタイムアウトを超える前に SDK から送信された最初と最後のデータヒットに基づいています。通常、レポートスイートのセッションタイムアウトは 30 分に設定されます。訪問回数は従来の Web 分析から取得されますが、これらのヒットは、ユーザーがアプリに入ってくる方法とアプリから出る方法について、引き続き貴重なインサイトを提供します。

## メッセージ {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### プッシュ通知には、サイズやその他の制限はありますか？

プッシュ通知メッセージには、140 文字の制限があります。送信またはスケジュールできる通知の数や、通知の送信頻度に制限はありません。

### プッシュ通知のカスタムペイロードはサポートされますか？

はい、JSON でコード化できるカスタムプッシュペイロードを提供しています。Android と iOS のペイロードは、それぞれ 4KB と 2KB に制限されています。これらのペイロードは、プッシュ通知またはローカル通知を介してアプリに送信されます。詳しくは、「[エクスペリエンス：プッシュメッセージ](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)」を参照してください。

### アプリ内メッセージにサイズ制限はありますか？

Adobe Mobile Services で作成された、公開済みのアクティブなアプリ内メッセージは、サーバー上でホストされ、アプリレポートスイートあたり 15MB のサイズ制限が適用されます。この制限は Adobe でホストされるメッセージコンテンツとリソースに適用されますが、他のホストやアプリ内で、アプリ内メッセージが参照するリソースには制限はありません。

### アプリ内メッセージに独自の HTML を使用することはできますか？

はい、アプリ内メッセージではカスタム HTML をサポートしています。詳しくは、「[エクスペリエンス：アプリ内メッセージ](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)」を参照してください。

### プッシュ通知やアプリ内メッセージの送信に使用できるトリガーは何ですか？

マーケターは、アプリ内メッセージを表示するトリガーとして送信される、Analytics データまたはイベントを選択できます。アプリ内メッセージは、デバイス上でローカルに発生するトリガーを使用します。複数のトリガーを選択している場合、メッセージが表示されるのと同じヒットで発生する必要があります。詳しくは、「[エクスペリエンス：アプリ内メッセージ](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md)」を参照してください。

プッシュメッセージは、以前から存在する Adobe Analytics セグメントまたは既に収集された Analytics 履歴データを基に作成されたカスタムセグメントを使用して送信されます。詳しくは、「[エクスペリエンス：プッシュメッセージ](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md)」を参照してください。

### 入力したアプリ内、プッシュまたはマーケティングリンク名でエラーが発生するのはなぜですか？

同じ親レポートスイートまたは VRS を使用する複数のアプリで、同じアプリ内メッセージ、プッシュメッセージまたはマーケティングリンク名を使用することはできません。この問題を解決するには、アプリ内メッセージ、プッシュメッセージまたはマーケティングリンクに別の名前を入力します。

## 場所 {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### 目標地点（POI）の数に制限はありますか？

特別な制限はありませんが、理想的なパフォーマンスおよびユーザーのデバイスのメモリ制限のために、POI を作成または更新するのは、最大で 5,000 までにすることをお勧めします。

## 獲得 {#section_B37F1129CD5843E890D0E54179455357}

### キャンペーンをアプリ内アクティビティに属性付けることはできますか。

はい。Adobe Mobile Services　は、アプリをプロモーションし、アプリにトラフィックを誘導して、獲得キャンペーンをアプリ内分析およびコンバージョンに結び付けるのに役立つ、マーケティングのテクニックを構築できるようサポートします。詳しくは、「[獲得](/help/using/acquisition-main/acquisition-main.md)」を参照してください。

### 新しいアプリユーザーを獲得しトラッキングするためのリンクを設定するにはどうしたらよいですか？

Apple App Store および Google Play からアプリケーションのダウンロードへとユーザーを誘導するマーケティングリンクを作成できます。これらのリンクを使用すると、単なるダウンロード回数に加えて、このリンク経由でアプリをダウンロードした後のユーザー行動（ライフサイクル系指標や成功イベント）を長期で追えるようになります。詳しくは、[マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)を参照してください。