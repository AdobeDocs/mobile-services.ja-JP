---
description: 'レポートスイートを設定し、Androidアプリデータを収集する前に、次の前提条件となるタスクを実行します '
seo-description: 'レポートスイートを設定し、Androidアプリデータを収集する前に、次の前提条件となるタスクを実行します '
seo-title: 事前準備
solution: Marketing Cloud,Analytics
title: 事前準備
topic: 開発者と導入
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Before you start {#before-you-start}

レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載される節のいずれかを完了します。
1. 各アプリ開発者の Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります。

>[!IMPORTANT]
>
>新しいレポートスイートを作成してSDKをダウンロードするには、Analytics管理者である必要があります。

### アプリ開発者

1. [役割固有のタスク](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)の「*Analytics 管理者*」の節に記載される手順を Analytics 管理者が完了していることを確認します。

1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載されるいずれかの節を Analytics 管理者が完了していることを確認します。
1. レポートスイートが設定されたら、[SDK のダウンロード](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46)に記載される手順を完了します。

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services UI には、以下のいずれかの方法でログインできます。

### Experience Cloud

Adobe ID を使用して [Experience Cloud](https://marketing.adobe.com) にログインします。この方法は、会社が Experience Cloud でプロビジョニングされていることと、お使いの Analytics アカウントがリンクされていることを前提としています。詳しくは、Experience cloudユーザーと [製品の管理を参照してください](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!TIP]
>
>会社がExperience cloudでプロビジョニングされているかどうか不明な場合は、既存のAdobe Analyticsアカウントを使用します。

### Adobe Analytics

「**[!UICONTROL Analytics アカウントでサインイン]**」をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1. Click **[!UICONTROL Create New App]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. アプリの名前を入力し、レポートスイートのタイプを選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。開発版と実稼働版では別個のレポートスイートおよびアプリを設定する必要があります。そのため、実稼働版を設定する準備が整ったら、これらの手順を繰り返します。
1. In **[!UICONTROL Report Suite ID]**, verify that your report suite name is displayed.
1. 「**[!UICONTROL 次の設定をコピー]**」で、**モバイルアプリのテンプレート[!UICONTROL が選択されていることを確認します。]**

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. Select your time zone, your currency, and click **[!UICONTROL Save]**.

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. Mobile Services UI にログインし、以下のいずれかの方法でアプリを開きます。

   * **[!UICONTROL アプリ一覧]ドロップダウンリストで、アプリを選択します。**
   * 右側のウィンドウで、アプリを見つけて開きます。

1. Click **[!UICONTROL Manage App Settings]**.
1. 「**[!UICONTROL アプリの SDK をダウンロード]」セクションにスクロールします。**
1. プラットフォームに応じた SDK とサンプルアプリをダウンロードします。

>[!TIP]
>
>アプリの設定ファイルはSDKのダウンロードに自動的に含まれるので、そのファイルを個別にダウンロードする必要はありません。 ただし、SDK を既にダウンロードしており、更新された設定を取得したい場合は、設定ファイルをもう一度ダウンロードしてください。

Android Studio を使用している場合は、アプリの `build.gradle` ファイルに以下のコードを追加することもできます。

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

次の情報に留意してください。

* コードサンプルのバージョン番号を Android SDK の適切なバージョンに置き換えてください。
* 設定ファイルをダウンロードして、プロジェクトにインクルードします。