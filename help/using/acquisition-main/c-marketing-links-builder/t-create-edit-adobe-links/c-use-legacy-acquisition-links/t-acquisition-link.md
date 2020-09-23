---
description: アプリをApple App StoreやGoogle Playから直接ダウンロードできるアプリストアリンクを作成できます。 作成したリンクは、ダウンロードの成功イベントを表します。
keywords: mobile
seo-description: アプリをApple App StoreやGoogle Playから直接ダウンロードできるアプリストアリンクを作成できます。 作成したリンクは、ダウンロードの成功イベントを表します。
seo-title: ダウンロード計測用リンクの作成
solution: Experience Cloud,Analytics
title: ダウンロード計測用リンクの作成
topic: Metrics
uuid: bb603013-fca9-44a2-820a-59e1c85d9444
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 74%

---


# ダウンロード計測用リンクの作成{#create-an-acquisition-link}

アプリをApple App StoreやGoogle Playから直接ダウンロードできるアプリストアリンクを作成できます。 作成したリンクは、ダウンロードの成功イベントを表します。

1. Click **[!UICONTROL Acquisition]** > **[!UICONTROL Manage Acquisition Links]** > **[!UICONTROL Create New]**.
1. **[!UICONTROL リンク情報]** セクションに次の情報を入力します。

   * （**必須**）アプリのリンクを説明する&#x200B;**[!UICONTROL 名前]**&#x200B;を指定します。
   * **[!UICONTROL トラッキングコード]**
目的のトラッキングコードを指定するか、**[!UICONTROL 生成]** をクリックして新しいトラッキングコードを作成します。
   * （**必須**）**[!UICONTROL ソース]**：「ニュースレター」または「ホームページ」など元のリファラーを指定します。
   * **[!UICONTROL メディア]**：「バナー」または「電子メール」など、マーケティングメディアを指定します。
   * **[!UICONTROL コンテンツ]**：リンクを持つ広告の名前または ID を指定します。
   * **[!UICONTROL 用語]**：広告に対する有料検索キーワードまたは他の検索キーワードを指定します。
   >[!IMPORTANT]
   >
   >ダウンロード計測用リンクの作成後に上述のフィールドの値を変更することはできません。

1. **[!UICONTROL アプリストアリンクを追加]** セクションのフィールドに情報を入力します。

   * **[!UICONTROL アプリストア]**

      アプリストアを選択します。
      * Apple App Store
      * Google Play

      以下に示すように、アプリストアごとに異なるオプションがあります。

   * **[!UICONTROL ブラウザーの地域（Apple App Store のみ）]**

      デスクトップのブラウザーに対して特定の地域のアプリストアを指定します。

      デスクトップのブラウザーでリンクをクリックした場合に表示されるページを定義できます。モバイルデバイスは、デバイスの設定に基づいて自動的にリダイレクトされます。

   * **[!UICONTROL ブラウザーの言語（Google Language（Google Play のみ））]**

      ドロップダウンリストから言語を選択します。

      デスクトップのブラウザーに対して Google Play Store で表示する言語を定義できます。モバイルデバイスは、デバイスの設定に基づいて言語を表示します。

   * **[!UICONTROL 名前で検索]**

      * Apple App Store では、アプリ ID がわからない場合、名前でアプリを検索できます。

         **[!UICONTROL 地域]** ドロップダウンリストからオプションの地域を選択して、検索を制限できます。

      * Google Play では、パッケージ名がわからない場合、名前でアプリを検索できます。
   * **[!UICONTROL アプリ ID（Apple App Store のみ）]**

      アプリを検索した場合、このフィールドは自動的に設定されます。アプリを検索せずに、アプリ ID の値を直接入力できます。

   * **[!UICONTROL パッケージ名（Google Play のみ）]**

      アプリを検索した場合、このフィールドは自動的に設定されます。検索する代わりに、「パッケージ名」の値を直接入力することもできます。



1. To save your configuration and to generate the link, click **[!UICONTROL Add]** > **[!UICONTROL Save]**.

   新規作成されたリンクが **[!UICONTROL App Store リンク]** セクションに表示されます。

   ![ストアリンク](assets/apps_store_links.png)

1. 「![リンクをコピー](assets/icon_clipboard.png)」をクリックして、追跡対象のリンクをクリップボードにコピーします。

1. ソーシャルメディアの投稿、広告、電子メールメッセージなどにリンクを貼り付けます。