---
description: Web またはアプリ内のディープリンクにユーザーを導く、新しいリンク先を作成できます。
keywords: モバイル
seo-description: Web またはアプリ内のディープリンクにユーザーを導く、新しいリンク先を作成できます。
seo-title: 新しいリンク先の作成
solution: Marketing Cloud、Analytics
title: 新しいリンク先の作成
topic: 指標
uuid: 390e3dea-0221-4f97-980d- a90ca9f162fa
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 新しいリンク先の作成 {#create-new-link-destination}

Web またはアプリ内のディープリンクにユーザーを導く、新しいリンク先を作成できます。

1. In the Mobile Services UI, click **[!UICONTROL Manage Apps]**.
1. アプリの名前をクリックして、そのアプリのアプリの情報ページを表示します。
1. Click **[!UICONTROL Manage Link Destinations]**.
1. Click **[!UICONTROL Create New]**.
1. 次のフィールドに情報を入力します。
   * **[!UICONTROL タイトル]**

      アプリリンクの宛先にわかりやすい名前を入力します。タイトルは、Adobe Mobile Services UI のリンク先を管理ページにのみ表示されます。説明的な名前は、組織のメンバーがすばやく特定のリンク先を見つけて、目的のインサイトを得るのに役立ちます。

   * **[!UICONTROL リンクタイプ]**

      使用可能なリンクタイプのリストを次に示します。

      * **[!UICONTROL アプリのディープリンク]**

         Provide a URI schema deep link (for example, `yourapp://section`). アプリのディープリンク先は、アプリ内のディープリンクにユーザーを誘導する、URI スキーマのディープリンクです。例えば、ユーザーをオンライン小売業者のモバイルアプリにある特定の製品ラインに誘導できます。

      * **[!UICONTROL Web リンク]**

         Type a web HTTP or HTTPS URL, for example,`https://adobe.com`. Web リンク先は、URL にユーザーを誘導します。例えば、ユーザーをオンライン小売業者の Web サイト上の製品ラインに誘導できます。

      * **[!UICONTROL ハイブリッドリンク]**

         iOS ユニバーサルリンクまたは Android アプリリンクを入力します（例：`https://yourwebsite.com`）。ハイブリッドリンクは、iOS Universal Links または Android App Links をサポートします。
   * **[!UICONTROL アプリ]**&#x200B;提供するリンクに関連付けられているアプリを選択します。

      >[!TIP]
      >
      >This information is required only if you selected an App Deep Link or a Hybrid Link in **[!UICONTROL Link Type]**. アプリが選択リストに表示されない場合、「**[!UICONTROL 新しいアプリを追加]」をクリックして、アプリストアから新しいアプリを参照します。**

   * **[!UICONTROL リンクタイプ]**

      選択したリンクの実際のURLを入力します。このフィールドのラベルは、選択したリンクのタイプに応じて変わります。

   * **[!UICONTROL 備考]**

      リンク先に関するオプションのメモを入力します。追加のメモは、Adobe Mobile Services UI のリンク先を管理ページにのみ表示されます。追加のメモは、組織のメンバーがすばやく特定のリンク先を見つけて目的のインサイトを得たり、関連するキャンペーンを示したり、その他の重要な項目を提示するのに役立ちます。


1. 「**保存**」をクリックします。
