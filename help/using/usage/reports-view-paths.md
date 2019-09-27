---
description: ビューパスレポートはパス分析に基づいたもので、アプリ内の状態間の移行時にたどったパスを表す遷移チャートを表示します。
keywords: モバイル
seo-description: ビューパスレポートはパス分析に基づいたもので、アプリ内の状態間の移行時にたどったパスを表す遷移チャートを表示します。
seo-title: パスレポートの表示
solution: Marketing Cloud,Analytics
title: パスレポートの表示
topic: レポート, 指標
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# パスレポートの表示 {#view-paths}

**[!UICONTROL ビューパス]レポートはパス分析に基づいたもので、アプリ内の状態間の移行時にたどったパスを表す遷移チャートを表示します。**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. **[!UICONTROL ビューパス]レポートでは、アプリにおけるユーザーの画面間の遷移を確認できます。****[!UICONTROL ビューアクション]レポートは、ユーザーがアプリでおこなう一連のアクション（クリック、選択、サイズ変更などのイベント）を表示します。**&#x200B;ファネルレポートを使用すると、ナビゲーションとアクションを1つのレポートで組み合わせることができます。 For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![ビューパス](assets/view_paths.png)

ボックスのような形状をした各ノードは、ユーザーがアプリを操作したときにたどったパスの特定の状態を表しています。例えば、上の図では、一番上のノードはアプリを起動し、メインビューに移動したユーザーの数を表しています。

ノードをクリックすると、「**[!UICONTROL フォーカス]**」や「**展開]」など、チャートを変更するための追加のオプションが表示されます。[!UICONTROL **&#x200B;例えば、一番上のノードの「**[!UICONTROL MainView]**」状態をクリックすると、「**[!UICONTROL フォーカス]」アイコンと「**&#x200B;展開]」アイコンが表示されます。**[!UICONTROL **

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. 次の図では、状態 1 でアプリを起動し、状態 2 でアプリのメインページを表示しています。状態 3 には、ユーザーがたどった次のパスが含まれています。

* カメラロールに移動
* アイテムセレクターに移動
* カメラに移動
* アイテム情報ページに移動

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. 次の図では、次のパスがアプリのメインビューを表示していたユーザーに先行します。

* アイテム情報
* アイテムセレクター
* カメラロール
* カメラ

![パスフォーカスの表示](assets/view_paths_focus.png)

複数のノードをフォーカスまたは展開することで、ユーザーがアプリ内でたどったパスを詳細に表示できます。以下に例を示します。

![ビューパスマルチ](assets/view_paths_mult.png)

このレポートでは、次のオプションを設定できます。

* **[!UICONTROL 期間]**&#x200B;カレンダー **[!UICONTROL アイコンをク]** リックし、カスタム期間を選択するか、ドロップダウンリストからプリセット期間を選択します。
* **[!UICONTROL Customize
Customize your reports by changing the Show By options, adding metrics and filters, and adding additional series (metrics), and more.]****** For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filter
Click Filter to create a filter that spans different reports to see how a segment is performing across all mobile reports.]******&#x200B;共通フィルターを定義すると、パス（画面遷移）レポート以外のすべてのレポートに適用できます。For more information, see Add Sticky Filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)
* **[!UICONTROL Download]**
Click **[!UICONTROL PDF]** or **[!UICONTROL CSV]** to download or open documents and share with users who do not have access to Mobile Services or to use the file in presentations.