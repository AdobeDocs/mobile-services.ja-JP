---
description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
keywords: mobile
seo-description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
seo-title: レポートへのフィルターの追加
solution: Experience Cloud,Analytics
title: レポートへのフィルターの追加
topic: Reports,Metrics
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 70%

---


# レポートへのフィルターの追加{#add-filters-to-reports}

この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。

>[!IMPORTANT]
>
>モバイルアプリ指標は、Reports &amp; Analytics、Ad Hoc Analysis、Data Warehouse およびその他の Analytics レポートインターフェイスでも使用できます。分類やレポートタイプが Adobe Mobile で使用できない場合、別のレポートインターフェイスを使用して生成できます。

この例では、**[!UICONTROL ユーザーとセッション]**&#x200B;レポートをカスタマイズしますが、説明はどのレポートにも当てはまります。

1. Open your app and click **[!UICONTROL Usage]** > **[!UICONTROL Users &amp; Sessions]**.

   ![](assets/customize1.png)

   このレポートは、アプリのユーザー数を時系列で表示します。 ただし、このアプリのiOS版とAndroid版の両方の指標は同じレポートスイートで収集されます。 ユーザー指標にカスタムフィルターを追加することで、モバイルOSごとにユーザーをセグメント化できます。

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

   このレポートには、ユーザーがオペレーティングシステム別に分類されて表示されるようになりました。 レポートのタイトルが、レポートに適用されたフィルターに合わせて変更されました。

   ![](assets/customize5.png)

   さらにレポートをカスタマイズできます。iOS 8.3 以降、iOS 8.3 オペレーティングシステムバージョンフィルターを使用して初回起動指標を追加することで、iOS 8.3 ユーザーがアプリをアップグレードして初回起動を実行した回数を確認できます。
1. **[!UICONTROL 初回起動]** で、**[!UICONTROL フィルターを追加]**／**[!UICONTROL ルールを追加]**&#x200B;をクリックし、ドロップダウンから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL iOS]** を選択します。
1. **[!UICONTROL および]** をクリックし、ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステムのバージョン]**／**[!UICONTROL iOS 8.3]** を選択します。

   フィルターはこの例のようになります。

   ![](assets/customize6.png)

1. **[!UICONTROL 更新]** および **[!UICONTROL 実行]** をクリックします。

   このレポートには、iOS 8.3を使用し、アプリを初めて起動したユーザーが表示されます。

   ![](assets/customize7.png)

   レポートのカスタマイズメニューの様々なオプションをテストし、お気に入りにブックマークを付けてください。 Adobe Mobile のレポートの URL を使用し、URL を電子メールで送信したり、お気に入りに追加したりできます。
