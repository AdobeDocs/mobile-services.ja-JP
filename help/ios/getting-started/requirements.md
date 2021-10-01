---
description: iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。
solution: Experience Cloud,Analytics
title: 事前準備
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 91%

---

# 事前準備 {#before-you-start}

iOS アプリデータを収集するようにレポートスイートを設定するには、次の手順を実行します。

## 役割固有のタスク {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](/help/ios/getting-started/getting-started.md)に記載される節のいずれかを完了します。
1. アプリ開発者ごとに Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります

>[!IMPORTANT]
>
>新しいレポートスイートを作成して SDK をダウンロードするには、Analytics 管理者である必要があります。

### アプリ開発者

1. 上記の「*Analytics 管理者*」の節に記載される手順を Analytics 管理者が完了していることを確認します。

1. 以下の「*Adobe Mobile Services UI へのログイン*」に記載されるいずれかの節を Analytics 管理者が完了していることを確認します。
1. レポートスイートが設定されたら、「*SDK のダウンロード*」の手順を実行します。

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン  {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services には、以下のいずれかの方法でログインできます。

* **Experience Cloud**

   Adobe ID を使用して [Experience Cloud](https://experience.adobe.com) にログインします。

   この方法は、会社がプロビジョニングされていることと、お使いの Analytics アカウントがリンクされていることを前提としています。プロビジョニングの詳細については、『Experience Cloud中央インターフェイスコンポーネントガイド』の「[Experience Cloudユーザーと製品の管理 ](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html)」を参照してください。 アカウントのリンクについて詳しくは、[Experience Cloudの組織 ](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html) を参照してください。

   >[!TIP]
   >
   >会社が Experience Cloud でプロビジョニングされているかどうかわからない場合は、既存の Adobe Analytics アカウントを使用してください。

* **Adobe Analytics**

   「**[!UICONTROL Analytics アカウントでログイン]**」をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1.  「**[!UICONTROL 新しいアプリを作成]**」をクリックします。

   このボタンが表示されない場合、**[!UICONTROL アプリ設定]**／**[!UICONTROL 追加]**&#x200B;をクリックします。

1. 「**[!UICONTROL レポートスイート]**」ドロップダウンで、「**[!UICONTROL 新しいレポートスイート]**」を選択します。

1. アプリの名前を入力し、一意のレポートスイート ID を選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。開発バージョンと実稼動バージョン用に、別々のレポートスイートとアプリを設定する必要があります。実稼動バージョンを設定する準備が整ったら、次の手順を繰り返します。
1. 「**[!UICONTROL モバイルアプリのテンプレート]**」を選択したままにします。

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. **[!UICONTROL タイムゾーン]**&#x200B;と&#x200B;**[!UICONTROL 通貨]**&#x200B;を選択し、「**[!UICONTROL 保存]**」をクリックします。

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. Mobile Services にログインし、以下のいずれかの方法でアプリを開きます。

   * 「**[!UICONTROL すべてのアプリ]**」ドロップダウンリストで、アプリを選択します。
   * 右側のウィンドウで、アプリを見つけて開きます。

1. 「**[!UICONTROL アプリ設定]**」をクリックします。
1. 「**[!UICONTROL アプリの SDK をダウンロード]**」セクションで、「**[!UICONTROL アプリの SDK をダウンロード]**」セクションまでスクロールします。

1. プラットフォームに応じた SDK とサンプルアプリをダウンロードします。

>[!TIP]
>
>アプリの設定ファイルは SDK ダウンロードに自動的に含まれます。そのため、別途ダウンロードする必要はありません。ただし、SDK を既にダウンロードしており、更新された設定を取得したい場合は、設定ファイルをもう一度ダウンロードしてください。
