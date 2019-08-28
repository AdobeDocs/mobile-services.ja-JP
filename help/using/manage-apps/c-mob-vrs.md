---
description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは1つのレポートスイートでデータを維持できますが、データを個別のレポートスイートにあるかのように管理することができます。
seo-description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは1つのレポートスイートでデータを維持できますが、データを個別のレポートスイートにあるかのように管理することができます。
seo-title: 仮想レポートスイート
title: 仮想レポートスイート
uuid: 3f467CAD-43e7-4cd0-889b-89f8c61fubbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは1つのレポートスイートでデータを維持できますが、データを個別のレポートスイートにあるかのように管理することができます。

VRSSを使用するアプリは、以下の機能を管理する以外に、通常のレポートスイートを使用するアプリと同様に機能します。

* 処理ルール
* evars/props/listvars/events
* タイムスタンプ対応オプション
* ディメンションフラグ（ライフサイクル、ロケーションなど）
* 分類 

これらの値は、親レポートスイートで管理され、同じ親レポートスイートに属する VRS と共有されます。

親レポートスイートに依存しないAdobe Mobile Services UIでは、次の領域にアクセスできます。

* 設定ファイル
* 目標地点の設定
* リンク先を管理
* ポストバックを管理
* メッセージリンク
* 獲得

VRSは、以下のタスクを完了するのに役立ちます。

* データアクセスの制限

   ある多国籍企業には、すべての地域用の 1 つのレポートスイートにデータを送信するアプリがあります。ただし、ある地域のビジネスユーザーが別の地域のデータを表示することを制限することを希望しています。会社の管理者は、地域ごとにユーザーをセグメント化し、その地域を管理するビジネスユーザーのみにVRSに対する権限を与えることができます。

   この制限は、ビジネスユーザーが自分の地域と無関係のデータを表示できないようにします。例えば、EMEAのビジネスユーザーは、APAC地域のデータを表示する必要はありません。

* 1つのレポートスイートに送信されるすべてのデータを使用して、アプリ内/プッシュメッセージング、場所のPOI、獲得およびポストバックを制御できます。

   ある多国籍企業は、すべての地域用の同じレポートスイートにすべてのデータを送信しようとしています。ただし、会社は、各地域のマーケティングチームが独自のアプリ内/プッシュメッセージを処理するように求めています。会社の管理者は地域のVRSSを作成でき、各チームはそのVRSに基づいて独自のアプリを管理できます。

   地域のチームは、VRS からの設定ファイルを使用してアプリを作成します。データは親レポートスイートに送信されますが、アプリ内/プッシュメッセージ、場所のPOI、獲得およびポストバックは、VRSから作成されたアプリで制御されます。

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Adobe Analyticsの管理者のみが、Adobe Analyticsの仮想レポートスイートを作成および変更できます。To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

各 VRS には一意の ID があります。Adobe Mobile Services UIで親レポートスイートIDを表示するには、アプリ設定を管理ページの **[!UICONTROL 「アプリの情報」]** セクションで、「詳細」をクリック ****&#x200B;します。

Adobe Mobile Services UI で、VRS を使用して、組織の特定のグループに対するアプリおよびセグメントデータを作成できます。これにより、例えば、スペインのビジネスユーザーは、日本のビジネスユーザーに関連するデータを確認できません。

>[!TIP]
>
>親レポートスイートから継承された値を変更することはできません。

VRS は、親レポートスイートに添付されたサーバー側セグメント定義です。SDK は親レポートスイートにのみヒットを送信し、次々にヒットを記録するので、結果として、VRS に対するデータ収集を実行できません。

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Adobe Mobile Servicesでは、親レポートスイートまたは仮想レポートスイートに基づいてアプリを作成できます。仮想レポートスイートに基づいてアプリを作成する場合、VRS セグメントをアプリの定義と合わせることをお勧めします。

>[!TIP]
>
>プッシュ証明書は、Mobile Services UIのアプリレベルで添付されます。

プッシュメッセージが正しく送信されたことを確認するには、オーディエンスセグメントが適切に定義されている必要があります。詳しくは、 [オーディエンス：プッシュメッセージ用のオーディエンスセグメントの定義および設定](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

アプリ設定ページのタイムゾーンプロパティは、Adobe AnalyticsでVRSを作成するために使用するタイムゾーンプロパティとは異なります。アプリ設定ページのプロパティは、親レポートスイートから継承され、Adobe Analytics にデータを送信するのに使用されます。Adobe AnalyticsでVRSを作成するときに指定するプロパティは、Mobile Services UIでレポートを表示し、親レポートスイートと異なる場合があります。

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

アプリを作成する際に VRS を使用するには、**アプリの情報ページのレポートスイート**&#x200B;ドロップダウンリストから VRS を選択します。このリストには、親および仮想レポートスイートが含まれています。

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

次に VRS のプロパティを示します。

>[!TIP]
>
>読み取り専用プロパティは親レポートスイートから継承されます。

| プロパティ | 親レポートスイートから継承 | 編集可能？ | メモ |
|--- |--- |--- |--- |
| `target.clientCode` | × | ○ |  |
| `target.timeout` | × | ○ |  |
| `audienceManager.server` | × | ○ |  |
| `audienceManager.analyticsForwardingEnabled` | ○ | ○ |  |
| `audienceManager.timeout` | × | ○ |  |
| `acquisition.server` | × | × |  |
| `acquisition.appid` | × | × |  |
| `analytics.rsids` | ○ | × |  |
| `analytics.server` | × | × |  |
| `analytics.ssl` | × | ○ |  |
| `analytics.offlineEnabled` | ○ |  |  |
| `analytics.charset` | ○ | × |  |
| `analytics.lifecycleTimeout` | × | ○ | ユーザーがデータの不整合を避けたい場合、親レポートスイートである必要があります。 |
| `analytics.privacyDefault` | × | ○ |  |
| `analytics.batchLimit` | × | ○ |  |
| `analytics.timezone` | ○ | ○（最初にアプリを作成する場合） | このタイムゾーンプロパティは、Adobe Analytics にデータを送信するために使用され、VRS の作成時に設定されたタイムゾーンプロパティとは異なります。 |
| `analytics.timezoneOffset` | ○ | × |  |
| `analytics.referrerTimeout` | × | ○ |  |
| `analytics.backdateSessionInfo` | ○ | ○ |  |

## 追加情報 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

仮想レポートスイートについて、次の情報を追加しました。

* VRS について詳しくは、[仮想レポートスイート](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)を参照してください。
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).