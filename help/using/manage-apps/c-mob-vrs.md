---
description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザは1つのレポートスイートにデータを保持しながら、別のレポートスイートにあるかのようにデータを管理できます。
seo-description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザは1つのレポートスイートにデータを保持しながら、別のレポートスイートにあるかのようにデータを管理できます。
seo-title: 仮想レポートスイート
title: 仮想レポートスイート
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザは1つのレポートスイートでデータを管理できますが、別のレポートスイートでデータを管理できるようになります。

VRSを使用するアプリは、次の機能を除き、通常のレポートスイートを使用するアプリと同じ動作をします。

* 処理ルール
* evars/props/listvars/events
* Timestamp-enabled option
* ディメンションフラグ（ライフサイクル、ロケーションなど）
* 分類 

これらの値は、親レポートスイートで管理され、同じ親レポートスイートに属する VRS と共有されます。

親レポートスイートとは別に、Adobe Mobile Services UIからは次の領域にアクセスできます。

* 設定ファイル
* 目標地点の設定
* リンク先を管理
* ポストバックを管理
* メッセージリンク
* 獲得

A VRS can help you complete the following tasks:

* データアクセスの制限

   ある多国籍企業には、すべての地域用の 1 つのレポートスイートにデータを送信するアプリがあります。However, the company wants to restrict the business user in one region from viewing the data in another region. 会社の管理者は、VRSを作成して、地域別にユーザーをセグメント化し、その地域を管理するビジネスユーザーにのみVRSへの権限を付与できます。

   この制限は、ビジネスユーザーが自分の地域と無関係のデータを表示できないようにします。例えば、EMEAのビジネスユーザーは、APAC地域のデータを確認する必要はありません。

* すべてのデータを1つのレポートスイートに送信して、アプリ内/プッシュメッセージ、場所のPOI、獲得およびポストバックを制御できます。

   ある多国籍企業は、すべての地域用の同じレポートスイートにすべてのデータを送信しようとしています。ただし、各地域のマーケティングチームが独自のアプリ内/プッシュメッセージを処理することを希望しています。 The company’s admin can create regional VRSs, and each team can manage their own app based on that VRS.

   地域のチームは、VRS からの設定ファイルを使用してアプリを作成します。データは親レポートスイートに送信されますが、アプリ内/プッシュメッセージ、ロケーションPOI、獲得およびポストバックは、VRSから作成されたアプリで制御されます。

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Adobe Analyticsで仮想レポートスイートを作成および変更できるのは、Adobe Analytics管理者のみです。 To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

各 VRS には一意の ID があります。To view the parent report suite ID in Adobe Mobile Services UI, on the Manage App Settings page, in the App Information section, click More Details.********

Adobe Mobile Services UI で、VRS を使用して、組織の特定のグループに対するアプリおよびセグメントデータを作成できます。これにより、例えば、スペインのビジネスユーザーは、日本のビジネスユーザーに関連するデータを確認できません。

>[!TIP]
>
>親レポートスイートから継承した値は変更できません。

VRS は、親レポートスイートに添付されたサーバー側セグメント定義です。SDK は親レポートスイートにのみヒットを送信し、次々にヒットを記録するので、結果として、VRS に対するデータ収集を実行できません。

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Adobe Mobile Servicesでは、親レポートスイートまたは仮想レポートスイートに基づくアプリを作成できます。 仮想レポートスイートに基づいてアプリを作成する場合、VRS セグメントをアプリの定義と合わせることをお勧めします。

>[!TIP]
>
>プッシュ証明書は、Mobile Services UIのアプリレベルで添付されます。

プッシュメッセージが正しく送信されたことを確認するには、オーディエンスセグメントが適切に定義されている必要があります。詳しくは、 [オーディエンス：プッシュメッセージ用のオーディエンスセグメントの定義および設定](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

The time zone property on the Manage App Settings page is different from the time zone property that you use to create the VRS in Adobe Analytics. アプリ設定ページのプロパティは、親レポートスイートから継承され、Adobe Analytics にデータを送信するのに使用されます。The property that you specify when you create the VRS in Adobe Analytics is used to display the reports in the Mobile Services UI and might be different from the parent report suite.

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

Here is some additional information about virtual report suites:

* VRS について詳しくは、[仮想レポートスイート](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)を参照してください。
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).