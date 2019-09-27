---
description: マーケティングリンクを作成または編集して、モバイルアプリやWebサイトへのディープリンクを提供できます。
keywords: モバイル
seo-description: You can create or edit Marketing Links to provide deep linking into your mobile app or your website.
seo-title: マーケティングリンクの作成または編集
solution: Marketing Cloud,Analytics
title: マーケティングリンクの作成または編集
topic: 指標
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

マーケティングリンクを作成または編集して、モバイルアプリやWebサイトへのディープリンクを提供できます。 For more information, see Apple Universal Links and Android App Links.[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. 次のどちらかのタスクを実行します。

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * リンクを編集するには、「**[!UICONTROL タイトル]」列でリンクの名前をクリックします。**

1. 次のフィールドに情報を入力します。

   * **[!UICONTROL マーケティングリンク名]**:

      (**Required**) Specify a descriptive name for your Marketing Link. 名前は、Adobe Mobile Services UI のマーケティングリンクページにのみ表示されます。説明的な名前は、組織のメンバーがすばやく特定のリンクを見つけて、目的のインサイトを得るのに役立ちます。

   * **[!UICONTROL 一意のトラッキングコード]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. トラッキングコードの使用を説明するレポートを表示できます。

   * **[!UICONTROL トラッキングコンテキストデータを追加]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. **[!UICONTROL カスタムコンテキストデータ]ドロップダウンリストで、プリセットタグまたはいずれかの独自のタグを選択します。**&#x200B;コンテキストデータは、マーケティングリンクが導入されたときのレポートに使用されます。

      次のプリセットタグを使用できます。

      * **Custom Context Data**
Specify the key and value. カスタムコンテキストデータを追加する場合、処理ルールを作成する必要があります。For more information, see Processing rules overview.[](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

      * **ソース**「ニュースレター」や「ホームページ」など、元のリファラーを指定します。

      * **Medium**
Specify the marketing medium, such as "banner" or "email."

      * **Content**
Specify the name or ID of the ad with the link.

      * **Term
Specify paid terms or other search terms for the ad.**
1. 「**[!UICONTROL 保存]**」をクリックします。
1. 次のフィールドに情報を入力します。

   * **（必須）** 「フォールバックURL ****」で、リンク先が一致しない場合にユーザーが送信されるURLを指定します（例えば、リンク先ルールに一致しないデスクトップまたは別のプラットフォーム上にいる場合）。
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      For more information, see Interstitials or Apple Universal Links and Android App Links.[](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

   * **（条件付き）** 「ユニバーサ **[!UICONTROL ルリンク」または「アプリリンク]******」が選択されている場合、「カスタムパス」で、ユーザーはクエリパラメーターを使用してドメインの後にURLパスを定義できます。 For more information, see Apple Universal Links and Android App Links.[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. アプリがインストールされている場合、インタースティシャルランディングページが表示されます。

   詳しくは、 [インタースティシャル](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. リンク先ページで、リンクを設定します。

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL 決定を追加]**
      * **[!UICONTROL パスを追加]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL オペレーティングシステム]**

         サポートされるオペレーティングシステムには、iOS、Android、AMX などが含まれます。

      * **[!UICONTROL デバイスタイプ]**

         デバイスタイプには、デスクトップ、電子書籍リーダー、ゲームコンソール、携帯電話、セットトップボックスなどのデバイスが含まれます。
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Web リンク]**
      * **[!UICONTROL アプリのディープリンク]**
      * **[!UICONTROL ハイブリッドリンク]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. 獲得を計測するには、「**[!UICONTROL アプリストア]」をリンク先のタイプとして使用します。**

      詳しくは、「新しいリンク先 [を作成する」を参照してください](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)。




1. マーケティングリンクを保存するには、「省略」 ![をクリックし](assets/icon_elipses.png) 、「保 **[!UICONTROL 存」をクリックします]**。
