---
description: iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。
seo-description: iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。
seo-title: 事前準備
solution: Marketing Cloud,Analytics
title: 事前準備
topic: 開発者と導入
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](/help/ios/getting-started/getting-started.md)に記載される節のいずれかを完了します。
1. 各アプリ開発者の Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります。

>[!IMPORTANT]
>
>新しいレポートスイートを作成してSDKをダウンロードするには、Analytics管理者である必要があります。

### アプリ開発者

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services には、以下のいずれかの方法でログインできます。

* **Experience Cloud**

   Adobe ID を使用して [Experience Cloud](https://marketing.adobe.com) にログインします。

   この方法は、会社がプロビジョニング済みで、Analyticsアカウントがリンク済みであることを前提としています。 For more information about provisioning, see [Manage Experience Cloud users and products](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html). For more information about linking your account, see Organizations and account linking.[](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)

   >[!TIP]
   >
   >会社がExperience cloudでプロビジョニングされているかどうか不明な場合は、既存のAdobe Analyticsアカウントを使用します。

* **Adobe Analytics**

   「**[!UICONTROL Analytics アカウントでサインイン]**」をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1. Click **[!UICONTROL Create New App]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. アプリの名前を入力し、一意のレポートスイート ID を選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。You need to set up separate report suites and apps for the development and production versions. When you are ready to set up the production version, repeat these steps.
1. 「**[!UICONTROL モバイルアプリのテンプレート]」を選択したままにします。**

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. Mobile Servicesにログインし、次のいずれかの方法でアプリを開きます。

   * **[!UICONTROL アプリ一覧]ドロップダウンリストで、アプリを選択します。**
   * 右側のウィンドウで、アプリを見つけて開きます。

1. Click **[!UICONTROL Manage App Settings]**.
1. 「**[!UICONTROL アプリの SDK をダウンロード]**」セクションで、「**アプリの SDK をダウンロード[!UICONTROL 」セクションまでスクロールします。]**

1. プラットフォームに応じた SDK とサンプルアプリをダウンロードします。

>[!TIP]
>
>アプリの設定ファイルはSDKのダウンロードに自動的に含まれるので、そのファイルを個別にダウンロードする必要はありません。 ただし、SDK を既にダウンロードしており、更新された設定を取得したい場合は、設定ファイルをもう一度ダウンロードしてください。

