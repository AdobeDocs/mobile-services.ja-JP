---
description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
keywords: モバイル
seo-description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
seo-title: レポートへのフィルターの追加
solution: Experience Cloud,Analytics
title: レポートへのフィルターの追加
topic: レポート, 指標
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: ht
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# レポートへのフィルターの追加{#add-filters-to-reports}

この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。

>[!IMPORTANT]
>
>モバイルアプリ指標は、Reports &amp; Analytics、Ad Hoc Analysis、Data Warehouse およびその他の Analytics レポートインターフェイスでも使用できます。分類やレポートタイプが Adobe Mobile で使用できない場合、別のレポートインターフェイスを使用して生成できます。

この例では、**[!UICONTROL ユーザーとセッション]**&#x200B;レポートをカスタマイズしますが、説明はどのレポートにも当てはまります。

1. アプリを開いて、**[!UICONTROL 使用状況]**／**[!UICONTROL ユーザーとセッション]**&#x200B;をクリックします。

   ![](assets/customize1.png)

   このレポートは、アプリのユーザー数を時系列で表示します。例えば、iOS バージョンと Android バージョンの両方のアプリの指標が同じレポートスイートで収集されている場合、ユーザー指標にカスタムフィルターを追加して、モバイル OS 別にユーザーをセグメント化できます。

1. **[!UICONTROL カスタマイズ]** をクリックします。

   ![](assets/customize2.png)

1. **[!UICONTROL ユーザー]** で、**[!UICONTROL フィルターを追加]**／**[!UICONTROL ルールを追加]**&#x200B;をクリックします。

1. ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL iOS]** を選択します。

   ![](assets/customize3.png)

   Android をフィルターとして追加するには、この手順を繰り返す必要があります。

1. **[!UICONTROL および]** をクリックし、ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL Android]** を選択します。

   フィルターは次の例のようになります。

   ![](assets/customize4.png)

1. **[!UICONTROL 更新]** をクリックします。
1. レポートを再生成するには、**[!UICONTROL 実行]** をクリックします。

   このレポートには、ユーザーがオペレーティングシステムごとに分類された形で表示されます。レポートのタイトルも、レポートに適用したフィルターに合わせて変更されます。

   ![](assets/customize5.png)

   さらにレポートをカスタマイズできます。iOS 8.3 以降、iOS 8.3 オペレーティングシステムバージョンフィルターを使用して初回起動指標を追加することで、iOS 8.3 ユーザーがアプリをアップグレードして初回起動を実行した回数を確認できます。
1. **[!UICONTROL 初回起動]** で、**[!UICONTROL フィルターを追加]**／**[!UICONTROL ルールを追加]**&#x200B;をクリックし、ドロップダウンから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL iOS]** を選択します。
1. **[!UICONTROL および]** をクリックし、ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステムのバージョン]**／**[!UICONTROL iOS 8.3]** を選択します。

   フィルターはこの例のようになります。

   ![](assets/customize6.png)

1. **[!UICONTROL 更新]** および **[!UICONTROL 実行]** をクリックします。

   このレポートには、アプリを初回起動した iOS 8.3 のユーザーが表示されます。

   ![](assets/customize7.png)

   レポートのカスタマイズメニューでいくつかのオプションをテストしてみてください。お気に入りのレポートは、ブックマークできます。Adobe Mobile のレポートの URL を使用し、URL を電子メールで送信したり、お気に入りに追加したりできます。
