---
description: タイプ（フルスクリーン、アラートまたは通知）および表示、テキストおよびボタンオプションを含む、アプリ内メッセージのエクスペリエンスオプションを設定します。
keywords: モバイル
seo-description: タイプ（フルスクリーン、アラートまたは通知）および表示、テキストおよびボタンオプションを含む、アプリ内メッセージのエクスペリエンスオプションを設定します。
seo-title: エクスペリエンスアプリ内メッセージ
solution: Marketing Cloud、Analytics
title: エクスペリエンスアプリ内メッセージ
topic: 指標
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

タイプ（フルスクリーン、アラートまたは通知）および表示、テキストおよびボタンオプションを含む、アプリ内メッセージのエクスペリエンスオプションを設定します。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. エクスペリエンスページで、メッセージの名前を入力します。
1. 「**[!UICONTROL タイプ]」セクションのフィールドに入力します。**

   * **[!UICONTROL タイプ]**&#x200B;アプリ内メッセージキャンペーンのメッセージタイプを選択します。

      * **[!UICONTROL フルスクリーン]**
      * **[!UICONTROL アラート]**
      * **[!UICONTROL ローカル通知]**
   * **[!UICONTROL テンプレート]**

      テーマの設定された応答メッセージテンプレートをコンテンツ用にカスタマイズします。

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL カスタム]**

      カスタム HTML コンテンツを読み込みます（全画面表示のみ）。クリックスルーリンクおよびキャンセルリンクを設置する必要があります。

      1. 「**[!UICONTROL 参照]」をクリックして HTML ファイルをダウンロードするか、HTML ドキュメントをウィンドウにドラッグします。**
      1. 「**[!UICONTROL 例をダウンロード]」をクリックすると、サンプルのカスタム HTML コンテンツが表示されます。**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. 「**[!UICONTROL 表示]」セクションのフィールドに入力します。**

   * **[!UICONTROL テーマ]**
   メッセージのテーマを選択します。

   * **[!UICONTROL レイアウト]**

      デバイス画面上のアプリのレイアウトを選択します。

   * **[!UICONTROL 画像 URL]**

      画像の URL。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL バンドルされている画像]**

      アプリコードバンドル内の画像へのパス。このオプションは、画像がない場合、または画像が使用できない場合に使用されます。例えば、デバイスがオフラインの場合は、画像は使用できない可能性があります。If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. 「**[!UICONTROL テキスト]」セクションのフィールドに入力します。**

   * **[!UICONTROL ヘッダー]**

      メッセージのヘッダー用のテキストを入力します。

   * **[!UICONTROL コンテンツ]**

      メッセージのコンテンツ用のテキストを入力します。

1. 「**[!UICONTROL ボタン]」セクションのフィールドに入力します。**

   * **[!UICONTROL クリックスルーボタン]**

      **[!UICONTROL クリックスルー]ボタンのラベル。**&#x200B;このボタンをタップすると、成功したクリックスルーとしてカウントされます。ユーザーが宛先にリダイレクトされます。

   * **[!UICONTROL 送信先]**

      メッセージをクリックスルーしたら、ユーザーを送る特定の宛先（Web、ディープまたはハイブリッドリンク）を選択します。成功したクリックスルーのリダイレクト URL。

      この URL には、次の情報を含めることができます。

      * `{userId}`ユーザー識別子に置換されるか、ユーザー識別子が設定されていない場合は空白です。
      * `{trackingId}`（s *_ vi* cookieと相関関係がある）に置き換えられます。
      * `{messageId}`を使用すると、アプリ内メッセージの一意のIDに置き換えられます。
      * `{lifetimeValue}`の値はライフタイム値に置き換えられ、ライフタイム値が存在しない場合は0になります。
      Here is an example of tracking the user ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. それ以外の場合、各プラットフォームでは、スキームがサポートされます。スキームを使用すると、アプリがカスタムスキームをサポートするように開発されている場合に、アプリを開いたり参照したりできます。

      >[!TIP]
      >
      >**[!UICONTROL Webリンクまた]** は **[!UICONTROL カスタムリンク]** の宛先タイプを使用すると、宛先タイプは追跡されません。「**[!UICONTROL ディープリンク]」のみが追跡されます。** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. （オプション）次のアイコンをクリックして、メッセージのレイアウトをプレビューします。

   * **[!UICONTROL 概要]** によりプレビューペインが非表示になります。

      ![プレビュー](assets/icon_preview.png) パネルを再表示するには、プレビューをクリックします。

   * **[!UICONTROL 方向の変更]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 腕時計の場合、方向は丸め面から四角い盤面に変わります。

   * **[!UICONTROL ユーザーの腕時計でのプレビュー]**

      ユーザーの腕時計に表示されるメッセージをプレビューするには ![、「監視アイコン](assets/icon_watch.png)」をクリックします。

   * **[!UICONTROL ユーザーの携帯電話でのプレビュー]**

      ユーザーの携帯電話のクリックアイコン ![に表示されるメッセージをプレビュー](assets/icon_phone.png)するには、

   * **[!UICONTROL ユーザーのタブレットでのプレビュー]**

      ユーザーのタブレットでメッセージをプレビューするには、タブレットアイコンをクリック ![](assets/icon_tablet.png)します。

      プレビューパネルの下部に、前の手順で選択したオーディエンスの説明を表示できます。前の手順で選択したオーディエンスの説明もプレビューパネルの下部に表示されます。

1. [スケジュールオプション](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)を設定します。
