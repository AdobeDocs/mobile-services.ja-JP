---
description: 'レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。 '
seo-description: 'レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。 '
seo-title: 事前準備
solution: Marketing Cloud,Analytics
title: 事前準備
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 3249a0f35807b230f8200e81772957fbb255832b

---


# 事前準備{#before-you-start}

レポートスイートを設定して Android アプリデータを収集する前に、前提条件のタスクを完了してください。

## 役割固有のタスク {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics 管理者およびアプリ開発者は、次のタスクを完了する必要があります。

### Analytics 管理者

レポートスイートを設定してモバイルアプリデータを収集するには、以下のようにします。

1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載される節のいずれかを完了します。
1. 各アプリ開発者の Analytics アカウントを作成します。

これで、アプリ開発者は作成されたレポートスイートにアクセスして表示できるようになります。

>[!IMPORTANT]
>
>新しいレポートスイートを作成して SDK をダウンロードするには、Analytics 管理者である必要があります。

### アプリ開発者

1. [役割固有のタスク](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)の「*Analytics 管理者*」の節に記載される手順を Analytics 管理者が完了していることを確認します。

1. [Adobe Mobile Services UI へのログイン](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)に記載されるいずれかの節を Analytics 管理者が完了していることを確認します。
1. レポートスイートが設定されたら、[SDK のダウンロード](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46)に記載される手順を完了します。

役割と権限について詳しくは、[役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)を参照してください。

## Adobe Mobile Services UI へのログイン  {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services は、モバイルアプリの分析およびターゲティングのための主要レポートインターフェイスです。これらの手順を完了すると、データ収集サーバー、レポートスイートなど、様々な設定が事前に構成された設定ファイルをダウンロードできます。

Adobe Mobile Services UI には、以下のいずれかの方法でログインできます。

### Experience Cloud

Adobe ID を使用して [Experience Cloud](https://marketing.adobe.com) にログインします。この方法は、会社が Experience Cloud でプロビジョニングされていることと、お使いの Analytics アカウントがリンクされていることを前提としています。詳しくは、「[Experience Cloud ユーザーと製品の管理](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)」を参照してください。

>[!TIP]
>
>会社が Experience Cloud でプロビジョニングされているかどうかわからない場合は、既存の Adobe Analytics アカウントを使用してください。

### Adobe Analytics

**[!UICONTROL Analytics アカウントでサインイン]**をクリックし、Analytics の会社名、ユーザー名、パスワードを入力します。

## レポートスイートの作成 {#section_7BC602ED1ABA42C6AB722F506B5219F3}

アプリのデータを収集し、アプリを定義するレポートスイートを作成するには、以下のようにします。

1. ブラウザーでhttps://mobilemarketing.adobe.com/と入力して、Mobile Services UIに [ログインします](https://mobilemarketing.adobe.com/) 。
1. Click **[!UICONTROL Create an App]**.

   このボタンが表示されない場合、**[!UICONTROL アプリ設定]**／**[!UICONTROL &#x200B;追加]**をクリックします。

1. **[!UICONTROL レポートスイート]**ドロップダウンで、**[!UICONTROL &#x200B;新しいレポートスイート]**を選択します。

1. アプリの名前を入力し、レポートスイートのタイプを選択します。

   例えば、`mycomobileappdev` などのレポートスイート ID です。開発版と実稼働版では別個のレポートスイートおよびアプリを設定する必要があります。そのため、実稼働版を設定する準備が整ったら、これらの手順を繰り返します。
1. **[!UICONTROL レポートスイート ID]**で、レポートスイートの名前が表示されていることを確認します。
1. **[!UICONTROL 次の設定をコピー]**で、**[!UICONTROL &#x200B;モバイルアプリのテンプレート]**が選択されていることを確認します。

   このテンプレートでタイムスタンプを有効にして、オフラインデータを収集することができます。また、モバイルソリューション変数をアクティベートして、ライフサイクル指標をキャプチャします。

1. タイムゾーンと通貨を選択し、**[!UICONTROL 保存]**をクリックします。

## SDK のダウンロード {#section_044C17DF82BC4FD8A3E409C456CE9A46}

モバイル SDK をダウンロードするには、以下のようにします。

1. ブラウザーにhttps://mobilemarketing.adobe.com/と入力して、Mobile Services UIに [ログインします](https://mobilemarketing.adobe.com/) 。
1. 左側のウィンドウで、「すべてのアプリ **[!UICONTROL 」ドロップダウンリスト]**をクリックし、アプリを選択します。
右側のパネルでアプリを選択することもできます。

   >[!IMPORTANT]
   >
   >右側のパネルにアプリを表示するには、まずアプリを作成する必要があります。 アプリの作成について詳しくは、新しいアプリの追 [加を参照してください](https://docs.adobe.com/content/help/en/mobile-services/using/manage-apps-ug/t-new-app.html)。

1. アプリの左側のウィンドウで、「アプリ設定を管理」 **[!UICONTROL をクリックします]**。
1. ページの下部で、「 **[!UICONTROL App SDKのダウンロード数」セクションまで下にスク]**ロールします。
1. プラットフォームに応じた SDK とサンプルアプリをダウンロードします。

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