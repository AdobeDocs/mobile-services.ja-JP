---
description: マーケティングリンクを作成または編集して、モバイルアプリやWebサイトへのディープリンクを提供できます。
keywords: モバイル
seo-description: マーケティングリンクを作成または編集して、モバイルアプリやWebサイトへのディープリンクを提供できます。
seo-title: マーケティングリンクの作成または編集
solution: Marketing Cloud、Analytics
title: マーケティングリンクの作成または編集
topic: 指標
uuid: 305a8265-38de-4d19-8c79- b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

マーケティングリンクを作成または編集して、モバイルアプリやWebサイトへのディープリンクを提供できます。詳しくは [、AppleユニバーサルリンクおよびAndroidアプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)を参照してください。

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. 次のどちらかのタスクを実行します。

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * リンクを編集するには、「**[!UICONTROL タイトル]」列でリンクの名前をクリックします。**

1. 次のフィールドに情報を入力します。

   * **[!UICONTROL マーケティングリンク名]**:

      (**Required**) Specify a descriptive name for your Marketing Link. 名前は、Adobe Mobile Services UI のマーケティングリンクページにのみ表示されます。説明的な名前は、組織のメンバーがすばやく特定のリンクを見つけて、目的のインサイトを得るのに役立ちます。

   * **[!UICONTROL 一意のトラッキングコード]**:

      **（必須**）目的のトラッキングコードを指定するか、またはクリック![して、新しい](assets/icon_generate.png) トラッキングコードを作成します。トラッキングコードの使用を説明するレポートを表示できます。

   * **[!UICONTROL トラッキングコンテキストデータを追加]**:

      **（オプション**） **[!UICONTROL "+]** 」アイコンをクリックし、コンテキストデータを使用してキャンペーンを追跡するための関連情報を入力します。**[!UICONTROL カスタムコンテキストデータ]ドロップダウンリストで、プリセットタグまたはいずれかの独自のタグを選択します。**&#x200B;コンテキストデータは、マーケティングリンクがデプロイされたときにレポートに使用されます。

      次のプリセットタグを使用できます。

      * **カスタムコンテキストデータ**&#x200B;キーと値を指定します。カスタムコンテキストデータを追加する場合、処理ルールを作成する必要があります。詳しくは [、処理ルールの概要](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)を参照してください。

      * **ソース**「ニュースレター」や「ホームページ」など、オリジナルリファラーを指定します。

      * **Medium**「バナー」や「電子メール」など、マーケティングメディアを指定します。

      * **コンテンツ**&#x200B;リンクを持つ広告の名前またはIDを指定します。

      * **キーワード**&#x200B;広告の有料キーワードまたはその他の検索用語を指定します。
1. 「**[!UICONTROL 保存]**」をクリックします。
1. 次のフィールドに情報を入力します。

   * **（必須）****[!UICONTROL フォールバックURL]**&#x200B;で、宛先が一致しない場合にユーザーが転送するURLを指定します（例えば、ユーザーがデスクトップにいる場合や、ターゲットルールに一致しない別のプラットフォームにいる場合）。
   * **[!UICONTROL 「マーケティングリンクオプション]**»で、??«インタースティシャル??»または??«ユニバーサル&#x200B;********

      詳しくは [、インタースティシャル](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) または [AppleユニバーサルリンクとAndroidアプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)を参照してください。

   * **（オプション）****[!UICONTROL 「ユニバーサル」または「アプリリンク]** 」が選択されている **[!UICONTROL 場合、]**&#x200B;ユーザーは、任意のクエリパラメーターを使用してドメインの後にURLパスを定義できます。詳しくは [、AppleユニバーサルリンクおよびAndroidアプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)を参照してください。

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   **（オプション**）複数の宛先がある場合、モバイルアプリがインストールされているかどうかに応じて、ユーザーをルーティングできます。アプリがインストールされている場合、インタースティシャルランディングページが表示されます。

   詳しくは、 [インタースティシャル](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. **[!UICONTROL 「保存]** 」をクリックし、「 **[!UICONTROL 次へ]**」をクリックします。
1. リンク先ページで、リンクを設定します。

   1. **[!UICONTROL デシジョンアイコン]** （![デシジョンアイコン](assets/icon_decision.png)）をクリックし、次のいずれかの決定場所を選択します。

      * **[!UICONTROL 決定を追加]**
      * **[!UICONTROL パスを追加]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL オペレーティングシステム]**

         サポートされるオペレーティングシステムには、iOS、Android、AMX などが含まれます。

      * **[!UICONTROL デバイスタイプ]**

         デバイスタイプには、デスクトップ、電子書籍リーダー、ゲームコンソール、携帯電話、セットトップボックスなどのデバイスが含まれます。
   1. **[!UICONTROL 目的]** のアイコン（ ![正方形アイコン](assets/icon_square.png) ）をクリックし、次のいずれかの宛先タイプを選択します。

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Web リンク]**
      * **[!UICONTROL アプリのディープリンク]**
      * **[!UICONTROL ハイブリッドリンク]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. 獲得を計測するには、「**[!UICONTROL アプリストア]」をリンク先のタイプとして使用します。**

      詳しくは、新しいリンク先の [作成](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)を参照してください。




1. マーケティングリンクを保存するには、 ![「省略記号»をクリック?してから??«保存??](assets/icon_elipses.png)****
