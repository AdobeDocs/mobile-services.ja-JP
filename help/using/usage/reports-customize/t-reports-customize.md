---
description: この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。
keywords: モバイル
solution: Experience Cloud,Analytics
title: レポートへのフィルターの追加
topic-fix: Reports,Metrics
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
exl-id: eb0589e9-668e-42d7-8f7a-00d7f0a2e3ff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%

---

# レポートへのフィルターの追加 {#add-filters-to-reports}

この情報は、フィルター（セグメント）を追加して組み込みのレポートをカスタマイズするのに役立ちます。

>[!IMPORTANT]
>
>モバイルアプリ指標は、Reports &amp; Analytics、Ad Hoc Analysis、Data Warehouse およびその他の Analytics レポートインターフェイスでも使用できます。分類やレポートタイプが Adobe Mobile で使用できない場合、別のレポートインターフェイスを使用して生成できます。

この例では、**[!UICONTROL ユーザーとセッション]**&#x200B;レポートをカスタマイズしますが、説明はどのレポートにも当てはまります。

1. アプリを開いて、「**[!UICONTROL 使用状況]**／**[!UICONTROL ユーザーとセッション]**」をクリックします。

   ![](assets/customize1.png)

   このレポートは、アプリのユーザーを完全な時系列で表示します。ただし、このアプリの iOS 版と Android 版の両方の指標は、同じレポートスイートで収集されます。ユーザー指標にカスタムフィルターを追加することで、モバイル OS ごとにユーザーをセグメント化できます。

1. 「**[!UICONTROL カスタマイズ]**」をクリックします。

   ![](assets/customize2.png)

1. 「**[!UICONTROL ユーザー]**」で、**[!UICONTROL フィルターを追加]**／**[!UICONTROL ルールを追加]**&#x200B;をクリックします。

1. ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL iOS]** を選択します。

   ![](assets/customize3.png)

   Android をフィルターとして追加するには、この手順を繰り返す必要があります。

1. 「**[!UICONTROL AND]**」をクリックし、ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL Android]** を選択します。

   フィルターは次の例のようになります。

   ![](assets/customize4.png)

1. 「**[!UICONTROL 更新]**」をクリックします。
1. レポートを再生成するには、「**[!UICONTROL 実行]**」をクリックします。

   ユーザーがオペレーティングシステム別に分類されて、レポートに表示されるようになりました。レポートのタイトルは、レポートに適用されたフィルターに合わせて変更されました。

   ![](assets/customize5.png)

   さらにレポートをカスタマイズできます。iOS 8.3 以降、iOS 8.3 オペレーティングシステムバージョンフィルターを使用して初回起動指標を追加することで、iOS 8.3 ユーザーがアプリをアップグレードして初回起動を実行した回数を確認できます。
1. 「**[!UICONTROL 初回起動]**」で、**[!UICONTROL フィルターを追加]**／**[!UICONTROL ルールを追加]**&#x200B;をクリックし、ドロップダウンから&#x200B;**[!UICONTROL オペレーティングシステム]**／**[!UICONTROL iOS]** を選択します。
1. **[!UICONTROL および]** をクリックし、ドロップダウンリストから&#x200B;**[!UICONTROL オペレーティングシステムのバージョン]**／**[!UICONTROL iOS 8.3]** を選択します。

   フィルターはこの例のようになります。

   ![](assets/customize6.png)

1. 「**[!UICONTROL 更新]**」および「**[!UICONTROL 実行]**」をクリックします。

   このレポートには、iOS 8.3 を使用し、アプリを初めて起動したユーザーがレポートに表示されるようになりました。

   ![](assets/customize7.png)

   しばらく時間をかけてレポートのカスタマイズメニューの様々なオプションをテストし、お気に入りをブックマークに追加してください。Adobe Mobile のレポートの URL を使用し、URL を電子メールで送信したり、お気に入りに追加したりできます。
