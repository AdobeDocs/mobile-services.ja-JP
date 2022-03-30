---
description: 'レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。 '
solution: Experience Cloud Services,Analytics
title: 事前準備
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 96%

---

# 事前準備 {#before-you-start}

レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。

## 役割固有のタスク {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載される節のいずれかを完了します。
1. アプリ開発者ごとに Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります

>[!IMPORTANT]
>
>新しいレポートスイートを作成して SDK をダウンロードするには、Analytics 管理者である必要があります。

### アプリ開発者

1. [役割固有のタスク](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)の「*Analytics 管理者*」に記載される手順を Analytics 管理者が完了していることを確認します。
1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載されるいずれかの節を Analytics 管理者が完了していることを確認します。
1. レポートスイートが設定されたら、[SDK のダウンロード](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46)の手順を完了します。

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン  {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services UI には、以下のいずれかの方法でログインできます。

### Experience Cloud

Adobe ID を使用して [Experience Cloud](https://experiencecloud.adobe.com) にログインします。この方法は、会社が Experience Cloud でプロビジョニングされていることと、お使いの Analytics アカウントがリンクされていることを前提としています。詳しくは、 [Experience Cloudユーザーと製品を管理する](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ja) (『Experience Cloud中央インターフェイスコンポーネント』ガイド ) を参照してください。

>[!TIP]
>
>会社が Experience Cloud でプロビジョニングされているかどうかわからない場合は、既存の Adobe Analytics アカウントを使用してください。

### Adobe Analytics

「**[!UICONTROL Analytics アカウントでログイン]**」をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1. にログインします。 [AdobeMobile Services](https://mobilemarketing.adobe.com).
1. 「**[!UICONTROL アプリケーションを作成]**」をクリックします。

   このボタンが表示されない場合、**[!UICONTROL アプリ設定]**／**[!UICONTROL 追加]**&#x200B;をクリックします。

1. 「**[!UICONTROL レポートスイート]**」ドロップダウンで、「**[!UICONTROL 新しいレポートスイート]**」を選択します。

1. アプリの名前を入力し、レポートスイートのタイプを選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。開発版と実稼働版では別個のレポートスイートおよびアプリを設定する必要があります。そのため、実稼働版を設定する準備が整ったら、これらの手順を繰り返します。
1.  「**[!UICONTROL レポートスイート ID]**」で、レポートスイートの名前が表示されていることを確認します。
1. 「**[!UICONTROL 次の設定をコピー]**」で、「**[!UICONTROL モバイルアプリのテンプレート]**」が選択されていることを確認します。

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. タイムゾーンと通貨を選択し、「**[!UICONTROL 保存]**」をクリックします。

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. ブラウザーに「[https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/)」と入力して Mobile Services UI にログインします。
1. 左側のパネルで、「**[!UICONTROL すべてのアプリケーション]**」ドロップダウンリストをクリックし、アプリケーションを選択します。また、右側のパネルでアプリケーションを選択することもできます。

   >[!IMPORTANT]
   >
   >右側のパネルにアプリケーションを表示するには、まずアプリケーションを作成する必要があります。アプリケーションの作成について詳しくは、[新しいアプリケーションの追加](/help/using/manage-apps/t-new-app.md)を参照してください。

1. アプリケーションの左側のウィンドウで、「**[!UICONTROL アプリケーションの設定を管理]**」をクリックします。

   >[!IMPORTANT]
   >
   >「**[!UICONTROL アプリケーションの設定を管理]**」オプションが表示されない場合は、Adobe Mobile Services にログインしていることを確認します。検証するには、ページの右上にある「![ソリューション切り替え](assets/solution-switcher.png)」アイコンをクリックし、**[!UICONTROL Adobe Mobile Services]** が左上に表示されていることを確認します。

1. 「アプリケーションの設定を管理」ページの下部にある「**[!UICONTROL アプリケーション SDK のダウンロード]**」セクションで、お使いのプラットフォーム用の SDK とサンプルアプリケーションをダウンロードします。

>[!TIP]
>
>アプリの設定ファイルは SDK ダウンロードに自動的に含まれます。そのため、別途ダウンロードする必要はありません。ただし、SDK を既にダウンロードしており、更新された設定を取得したい場合は、設定ファイルをもう一度ダウンロードしてください。

Android Studio を使用している場合は、アプリの `build.gradle` ファイルに以下のコードを追加することもできます。

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

次の情報に留意してください。

* コードサンプルのバージョン番号を Android SDK の適切なバージョンに置き換えてください。
* 設定ファイルをダウンロードして、プロジェクトにインクルードします。
