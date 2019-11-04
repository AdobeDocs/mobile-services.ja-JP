---
description: iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。
seo-description: iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。
seo-title: 事前準備
solution: Experience Cloud,Analytics
title: 事前準備
topic: 開発者と導入
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 事前準備{#before-you-start}

iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。

## 役割固有のタスク {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](/help/ios/getting-started/getting-started.md)に記載される節のいずれかを完了します。
1. 各アプリ開発者の Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります。

>[!IMPORTANT]
>
>新しいレポートスイートを作成して SDK をダウンロードするには、Analytics 管理者である必要があります。

### アプリ開発者

1. 上記の「*Analytics 管理者*」の節に記載される手順を Analytics 管理者が完了していることを確認します。

1. 以下の「*Adobe Mobile Services UI へのログイン*」に記載されるいずれかの節を Analytics 管理者が完了していることを確認します。
1. レポートスイートが設定されたら、「*SDK のダウンロード*」の手順を実行します。

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services には、以下のいずれかの方法でログインできます。

* **Experience Cloud**

   Adobe ID を使用して [Experience Cloud](https://marketing.adobe.com) にログインします。

   この方法は、会社がプロビジョニングされていることと、お使いの Analytics アカウントがリンクされていることを前提としています。プロビジョニングについて詳しくは、「[Experience Cloud のユーザーと製品の管理](https://docs.adobe.com/content/help/ja-JP/core-services/interface/manage-users-and-products/admin-getting-started.html)」を参照してください。アカウントのリンクについて詳しくは、「[組織とアカウントのリンク](https://docs.adobe.com/content/help/ja-JP/core-services/interface/manage-users-and-products/organizations.html)」を参照してください。

   >[!TIP]
   >
   >会社が Experience Cloud でプロビジョニングされているかどうかわからない場合は、既存の Adobe Analytics アカウントを使用してください。

* **Adobe Analytics**

   **[!UICONTROL Analytics アカウントでサインイン]**&#x200B;をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1. **[!UICONTROL 新しいアプリを作成]**&#x200B;をクリックします。

   このボタンが表示されない場合、**[!UICONTROL アプリ設定]**／**[!UICONTROL 追加]**&#x200B;をクリックします。

1. **[!UICONTROL レポートスイート]**&#x200B;ドロップダウンで、**[!UICONTROL 新しいレポートスイート]**&#x200B;を選択します。

1. アプリの名前を入力し、一意のレポートスイート ID を選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。開発バージョンと実稼働バージョン用に、別々のレポートスイートとアプリを設定する必要があります。実稼働バージョンを設定する準備が整ったら、次の手順を繰り返します。
1. **[!UICONTROL モバイルアプリのテンプレート]**&#x200B;を選択したままにします。

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. **[!UICONTROL タイムゾーン]**&#x200B;と&#x200B;**[!UICONTROL 通貨]**&#x200B;を選択し、**[!UICONTROL 保存]**&#x200B;をクリックします。

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. Mobile Services にログインし、以下のいずれかの方法でアプリを開きます。

   * **[!UICONTROL アプリ一覧]**&#x200B;ドロップダウンリストで、アプリを選択します。
   * 右側のウィンドウで、アプリを見つけて開きます。

1. **[!UICONTROL アプリ設定]**&#x200B;をクリックします。
1. **[!UICONTROL アプリの SDK をダウンロード]**&#x200B;セクションで、**[!UICONTROL アプリの SDK をダウンロード]**&#x200B;セクションまでスクロールします。

1. プラットフォームに応じた SDK とサンプルアプリをダウンロードします。

>[!TIP]
>
>アプリの設定ファイルは SDK ダウンロードに自動的に含まれます。そのため、別途ダウンロードする必要はありません。ただし、SDK を既にダウンロードしており、更新された設定を取得したい場合は、設定ファイルをもう一度ダウンロードしてください。

