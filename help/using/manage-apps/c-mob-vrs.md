---
description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは、1 つのレポートスイートにデータを維持して、別のレポートスイートにあるようにデータを管理できます。
seo-description: 仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは、1 つのレポートスイートにデータを維持して、別のレポートスイートにあるようにデータを管理できます。
seo-title: 仮想レポートスイート
title: 仮想レポートスイート
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 77%

---


# 仮想レポートスイート{#virtual-report-suites}

仮想レポートスイート（VRS）は、1 つまたは複数のセグメント定義をレポートスイートに適用することで作成されたレポートスイートです。これにより、ユーザーは、1 つのレポートスイートにデータを維持して、別のレポートスイートにあるようにデータを管理できます。

VRS を使用するアプリは、次の機能の管理を除いて、通常のレポートスイートを使用するアプリと同じ機能です。

* 処理ルール
* evars/props/listvars/イベント
* タイムスタンプ対応オプション
* Dimensionフラグ（ライフサイクル、場所など）
* 分類

これらの値は親レポートスイートで管理され、同じ親レポートスイートに属するVRSと共有されます。

次の領域は、親レポートスイートとは独立して、Adobe Mobile Services UI でアクセスできます。

* 設定ファイル
* 目標地点の設定
* リンク先を管理
* ポストバックを管理
* メッセージリンク
* 獲得

VRS は、次のタスクを実行するのに役立ちます。

* データアクセスの制限

   複数国籍の会社には、すべての地域に関するデータをレポートスイートに送信するアプリがあります。 ただし、その企業はビジネスユーザーを 1 つの地域に制限して、別の地域のデータを表示できないようにしたいと考えています。会社の管理者は、ユーザーを地域でセグメント化する VRS を作成して、その地域を管理するビジネスユーザーに対する VRS にのみ権限を付与できます。

   この制限は、ビジネスユーザーが自分の地域と無関係のデータを表示できないようにします。例えば、EMEA のビジネスユーザーは、APAC 地域のデータを確認する必要はありません。

* すべてのデータが 1 つのレポートスイートに送信されるアプリ内／プッシュメッセージ、ロケーション POI、獲得およびポストバックを制御できます。

   ある多国籍企業は、すべての地域用の同じレポートスイートにすべてのデータを送信しようとしています。ただし、この企業は、各地域から集まったマーケティングチームにそれぞれが担当するアプリ内／プッシュメッセージを処理させたいと考えています。会社の管理者が地域の VRS を作成し、各チームはその VRS に基づいて自分のアプリを管理できます。

   地域のチームは、VRS からの設定ファイルを使用してアプリを作成します。データは親レポートスイートに送信されますが、アプリ内／プッシュメッセージ、ロケーション POI、獲得およびポストバックは、VRS から作成されたアプリで制御されます。

## Adobe Analytics での仮想レポートスイートの作成 {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Adobe Analytics 管理者のみ、Adobe Analytics で仮想レポートスイートを作成および変更できます。仮想レポートスイートを作成するには、「[仮想レポートスイートの作成](https://docs.adobe.com/content/help/ja-JP/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html)」を参照してください。

各 VRS には一意の ID があります。親レポートスイート ID を Adobe Mobile Services UI で表示するには、アプリ設定ページの **[!UICONTROL アプリ情報]** セクションで、**[!UICONTROL さらに詳細を表示]** をクリックします。

AdobeのMobile Services UIでは、VRSを使用してアプリを作成し、データを組織内の特定のグループにセグメント化できます。 例えば、スペインのビジネスユーザーは、日本のビジネスユーザーに関連するデータを見ることができません。

>[!TIP]
>
>親レポートスイートから継承された値は変更できません。

VRSは、親レポートスイートに関連付けられるサーバー側のセグメント定義です。 その結果、SDKは親レポートスイートにのみヒットを送信し、その親レポートスイートはヒットを記録するので、VRSに対してデータ収集を実行できません。

## Adobe Mobile Services の仮想レポートスイートとデータ収集 {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

Adobe Mobile Services では、親レポートスイートまたは仮想レポートスイートに基づいてアプリを作成できます。仮想レポートスイートに基づいてアプリを作成する場合、VRS セグメントをアプリの定義と合わせることをお勧めします。

>[!TIP]
>
>プッシュ証明書は、Mobile Services UI のアプリレベルで添付されます。

プッシュメッセージが正しく送信されるように、オーディエンスセグメントを正しく定義する必要があります。 For more information, see [Audience: Define and Configure Audience Segments for Push Messages](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## タイムゾーンについて {#section_498E1EED22D741C3BDED44F01FACA72A}

アプリ設定ページのタイムゾーンプロパティは、Adobe Analytics で VRS を作成するために使用するタイムゾーンプロパティとは異なります。アプリ設定ページのプロパティは、親レポートスイートから継承され、Adobe Analytics にデータを送信するのに使用されます。Adobe Analytics で VRS を作成する際に指定するプロパティは、Mobile Services UI でレポートを表示するために使用され、親レポートスイートとは異なる可能性があります。

## Mobile Services UI での仮想レポートスイートの選択 {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

アプリを作成する際に VRS を使用するには、アプリの情報ページの&#x200B;**[!UICONTROL レポートスイート]**&#x200B;ドロップダウンリストから VRS を選択します。このリストには、親および仮想レポートスイートが含まれています。

>[!IMPORTANT]
>
>リストから VRS を選択するには、青い点が付き、`vrs_` *`<company_name>`*`_`*`<unique name>`*   命名規則を使用しているオプションを見つけます。

## 仮想レポートスイートのプロパティ {#section_20ECE6243F664C4FB4347ADB4FF0458A}

次に VRS のプロパティを示します。

>[!TIP]
>
>読み取り専用プロパティは、親レポートスイートから継承されます。

| プロパティ | 親レポートスイートから継承 | 編集可能？ | 備考 |
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
| `analytics.lifecycleTimeout` | × | ○ | 親レポートスイートにする必要があります。 |
| `analytics.privacyDefault` | × | ○ |  |
| `analytics.batchLimit` | × | ○ |  |
| `analytics.timezone` | ○ | はい、最初にアプリを作成したとき。 | このタイムゾーンプロパティは、データをAdobe Analyticsに送信するために使用され、VRSの作成時に設定されるタイムゾーンプロパティとは異なります。 |
| `analytics.timezoneOffset` | ○ | × |  |
| `analytics.referrerTimeout` | × | ○ |  |
| `analytics.backdateSessionInfo` | ○ | ○ |  |

## 追加情報 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

仮想レポートスイートに関する追加情報を以下に示します。

* VRS について詳しくは、[仮想レポートスイート](https://docs.adobe.com/content/help/ja-JP/analytics/components/virtual-report-suites/vrs-about.html)を参照してください。
* VRS の実装計画について詳しくは、「[仮想レポートスイートのワークフロー](https://docs.adobe.com/content/help/ja-JP/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html)」を参照してください。