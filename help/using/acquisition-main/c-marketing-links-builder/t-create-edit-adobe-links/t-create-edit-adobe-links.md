---
description: マーケティングリンクを作成または編集して、モバイルアプリまたは Web サイトへのディープリンクを提供できます。
keywords: mobile
seo-description: マーケティングリンクを作成または編集して、モバイルアプリまたは Web サイトへのディープリンクを提供できます。
seo-title: マーケティングリンクの作成または編集
solution: Experience Cloud,Analytics
title: マーケティングリンクの作成または編集
topic: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 94%

---


# マーケティングリンクの作成または編集{#create-or-edit-marketing-links}

マーケティングリンクを作成または編集して、モバイルアプリまたは Web サイトへのディープリンクを提供できます。詳しくは、「[Apple ユニバーサルリンクと Android アプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)」を参照してください。

1. アプリの左側のナビゲーションパネルで、**[!UICONTROL 獲得]** を展開して、**[!UICONTROL マーケティングリンクビルダー]** をクリックします。
1. 次のどちらかのタスクを実行します。

   * 新しいマーケティングリンクを作成するには、**[!UICONTROL 新規作成]** をクリックします。
   * リンクを編集するには、**[!UICONTROL タイトル]** 列でリンクの名前をクリックします。

1. 次のフィールドに情報を入力します。

   * **[!UICONTROL マーケティングリンク名]**：

      （**必須**）マーケティングリンクを説明する名前を指定します。名前は、Adobe Mobile Services UI のマーケティングリンクページにのみ表示されます。説明的な名前は、組織のメンバーがすばやく特定のリンクを見つけて、目的のインサイトを得るのに役立ちます。

   * **[!UICONTROL 一意のトラッキングコード]**：

      （**必須**）目的のトラッキングコードを指定するか、![生成アイコン](assets/icon_generate.png) をクリックして新しいトラッキングコードを作成します。トラッキングコードの使用を説明するレポートを表示できます。

   * **[!UICONTROL トラッキングコンテキストデータを追加]**：

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. **[!UICONTROL カスタムコンテキストデータ]**&#x200B;ドロップダウンリストで、プリセットタグまたはいずれかの独自のタグを選択します。コンテキストデータは、マーケティングリンクが表示される際のレポートに使用されます。

      次のプリセットタグを使用できます。

      * **カスタムコンテキスト**：データキーと値を指定します。カスタムコンテキストデータを追加する場合、処理ルールを作成する必要があります。詳しくは、「[処理ルールの概要](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

      * **ソース**：「ニュースレター」または「ホームページ」など、元のリファラーを指定します。

      * **メディア**：「バナー」または「電子メール」など、マーケティングメディアを指定します。

      * **コンテンツ**：リンクを持つ広告の名前または ID を指定します。

      * **用語**：広告に対する有料検索キーワードまたは他の検索キーワードを指定します。
1. 「**[!UICONTROL 保存]**」をクリックします。
1. 次のフィールドに情報を入力します。

   * （**必須**）**[!UICONTROL フォールバック URL]**&#x200B;で、リンク先が一致しない場合にユーザーが転送される URL を指定します（例えば、ユーザーがデスクトップにいるか、リンク先ルールに一致しない別のプラットフォームにいる場合）。
   * **[!UICONTROL マーケティングリンクオプション]** で、**[!UICONTROL インタースティシャル]** または **[!UICONTROL ユニバーサルリンクとアプリリンク]** を選択します。

      詳しくは、「[インタースティシャル](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)」または「[Apple ユニバーサルリンクと Android アプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)」を参照してください。

   * **（条件付き）****[!UICONTROL ユニバーサルリンクまたはアプリリンク]** が選択されている場合、**[!UICONTROL カスタムパス]**&#x200B;では、ユーザーは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。詳しくは、「[Apple ユニバーサルリンクと Android アプリリンク](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)」を参照してください。

1. **[!UICONTROL ディープリンクインタースティシャルを編集]** をクリックして、リンクを設定します。

   （**オプション**）複数のリンク先がある場合、モバイルアプリをインストールしているかどうかに応じてユーザーをルーティングできます。アプリケーションがインストールされている場合は、インタースティシャルランディングページが表示されます。

   For more information, see [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. **[!UICONTROL 保存]** をクリックしてから、**[!UICONTROL 次へ]** をクリックします。
1. リンク先ページで、リンクを設定します。

   1. **[!UICONTROL 決定]**&#x200B;アイコン（![決定アイコン](assets/icon_decision.png)）をクリックして、次のいずれかの決定の場所を選択します。

      * **[!UICONTROL 決定を追加]**
      * **[!UICONTROL パスを追加]**
   1. **[!UICONTROL 決定を追加]** を選択した場合、次のいずれかの決定タイプを選択します。

      * **[!UICONTROL オペレーティングシステム]**

         サポートされるオペレーティングシステムには、iOS、Android、AMX などが含まれます。

      * **[!UICONTROL Device Type]**

         デバイスタイプには、デスクトップ、電子書籍リーダー、ゲームコンソール、携帯電話、セットトップボックスなどのデバイスが含まれます。
   1. **[!UICONTROL リンク先]**&#x200B;アイコン（![正方形アイコン](assets/icon_square.png)）をクリックして、次のいずれかのリンク先タイプを選択します。

      * **[!UICONTROL アプリストア]**
      * **[!UICONTROL Web リンク]**
      * **[!UICONTROL アプリのディープリンク]**
      * **[!UICONTROL ハイブリッドリンク]**

      >[!TIP]
      >
      >アプリストアへのリンクのリンク先タイプとして **[!UICONTROL Web リンク]** を使用すると、獲得が計測されません。獲得を計測するには、**[!UICONTROL アプリストア]** をリンク先のタイプとして使用します。

      詳しくは、「[新しいリンク先を作成する](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)」を参照してください。




1. マーケティングリンクを保存するには、「![省略記号](assets/icon_elipses.png)」をクリックしてから、**[!UICONTROL 保存]** をクリックします。
