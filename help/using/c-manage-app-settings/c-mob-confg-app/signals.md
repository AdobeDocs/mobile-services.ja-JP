---
description: ポストバックを使用すると、Adobe Mobile によって収集されたデータを別のサードパーティサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように Mobile Services を設定できます。
seo-description: ポストバックを使用すると、Adobe Mobile によって収集されたデータを別のサードパーティサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように Mobile Services を設定できます。
seo-title: ポストバックの設定
title: ポストバックの設定
uuid: a026575c-057b-4868- b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

ポストバックを使用すると、Adobe Mobile によって収集されたデータを別のサードパーティサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように Mobile Services を設定できます。

>[!IMPORTANT]
>
>ポストバックを使用するには、4.6SDK以降をインストールする必要があります。詳しくは、「[Android - ポストバック](/help/android/analytics-main/postbacks/postbacks.md)」または「[iOS - ポストバック](/help/ios/analytics-main/postback/postback.md)」を参照してください。

1. 目的のアプリの名前をクリックして、そのアプリ設定ページに移動し、ページ右上端の「**ポストバックを管理**」リンクをクリックします。
1. Click **[!UICONTROL Create Postback]**.
1. フィールドに次の情報を入力します。

   * **[!UICONTROL ポストバックのタイプ]**

      **[!UICONTROL 「カスタム]**」を選択します。将来的にはテンプレートが使用可能になります。

   * **[!UICONTROL 名前]**

      ポストバックを説明する名前を指定します。

   * **[!UICONTROL URL]**

      有効なエンドポイントURLを指定します（GETリクエストの必要なクエリパラメーターを含む）。この URL は、データ送信先（広告サーバーまたは独自のエンドポイント）から取得します。`https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`例えば、

   * **[!UICONTROL コンテキスト変数]**

      URL の一部を強調表示し、ドロップダウンリストから目的のコンテキスト変数を選択します。また、コンテキスト変数をURLに挿入して、URLにヒットの値を持つすべてのテンプレート変数を置き換えることもできます。

   * **[!UICONTROL POST 本文を追加]**

      例えば POST リクエストに対してなど、追加の投稿本文のコンテンツがあれば指定します。投稿本文テキストを指定する場合は、投稿本文のコンテンツタイプを指定します。例：`application/json`。

   * **[!UICONTROL タイムアウト (秒単位)]**

      ポストバックを待機する時間（秒単位）を指定します。

   * **[!UICONTROL トリガー]**

      ポストバックをトリガーする 1 つまたは複数のデータタグおよび条件を指定します。For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. また、ポストバックをアクティブ化する指標を指定できます。For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL 特徴]**
   トリガーされたらメッセージが表示されるユーザーを指定します。Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. 「**[!UICONTROL 保存]**」をクリックしてポストバックを作成し、「**ポストバックを管理[!UICONTROL 」リストに追加します。]**

   将来的にポストバックをアクティブにするには、次のいずれかを実行します。

   * Select the checkbox next to the postback in the **[!UICONTROL Manage Postbacks]** list and click **[!UICONTROL Activate Selected]**.
   * 「**[!UICONTROL 保存とアクティブ化]」をクリックして変更内容を保存し、直ちにポストバックをアクティブにします。**
