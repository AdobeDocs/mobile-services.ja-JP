---
description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
keywords: モバイル
seo-description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
seo-title: レポートへのフィルターの追加
solution: Marketing Cloud,Analytics
title: レポートへのフィルターの追加
topic: レポート, 指標
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Add filters to reports{#add-filters-to-reports}

この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。

>[!IMPORTANT]
>
>モバイルアプリ指標は、Reports &amp; Analytics、Ad Hoc Analysis、Data Warehouseおよびその他のAnalyticsレポートインターフェイスでも使用できます。 分類やレポートタイプが Adobe Mobile で使用できない場合、別のレポートインターフェイスを使用して生成できます。

この例では、**[!UICONTROL ユーザーとセッション]レポートをカスタマイズしますが、説明はどのレポートにも当てはまります。**

1. Open your app and click **[!UICONTROL Usage]** &gt; **[!UICONTROL Users &amp; Sessions]**.

   ![](assets/customize1.png)

   このレポートは、アプリのユーザー数を時系列で表示します。例えば、iOS バージョンと Android バージョンの両方のアプリの指標が同じレポートスイートで収集されている場合、ユーザー指標にカスタムフィルターを追加して、モバイル OS 別にユーザーをセグメント化できます。

1. Click **[!UICONTROL Customize]**.

   ![](assets/customize2.png)

1. Under **[!UICONTROL Users]**, click **[!UICONTROL Add Filter]** and click **[!UICONTROL Add Rule]**.

1. Select **[!UICONTROL Operating Systems]**, and from the drop-down list, and select **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   Androidをフィルターとして追加するには、この手順を繰り返す必要があります。

1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL Android]**.

   フィルターは次の例のようになります。

   ![](assets/customize4.png)

1. Click **[!UICONTROL Update]**.
1. To regenerate the report, click **[!UICONTROL Run]**.

   このレポートには、ユーザーがオペレーティングシステムごとに分類された形で表示されます。レポートのタイトルも、レポートに適用したフィルターに合わせて変更されます。

   ![](assets/customize5.png)

   このレポートはさらにカスタマイズできます。 iOS 8.3から、iOS 8.3オペレーティングシステムバージョンフィルターを使用して初回起動指標を追加し、iOS 8.3のお客様がアプリをアップグレードして初回起動を実行した回数を確認できます。
1. Under **[!UICONTROL First Launches]**, click **[!UICONTROL Add Filter]**, click **[!UICONTROL Add Rule]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL iOS]**.
1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating System Versions]** from the drop-down list, and select **[!UICONTROL iOS 8.3]**.

   フィルターはこの例のようになります。

   ![](assets/customize6.png)

1. Click **[!UICONTROL Update]** and **[!UICONTROL Run]**.

   このレポートには、アプリを初回起動した iOS 8.3 のユーザーが表示されます。

   ![](assets/customize7.png)

   レポートのカスタマイズメニューでいくつかのオプションをテストしてみてください。お気に入りのレポートは、ブックマークできます。Adobe mobileのレポートURLは機能し、電子メールでお気に入りに追加できます。
