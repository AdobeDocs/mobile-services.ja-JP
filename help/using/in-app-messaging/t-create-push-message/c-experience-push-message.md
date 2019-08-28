---
description: 名前、メッセージテキストおよび宛先オプションを含む、プッシュメッセージおよびリッチプッシュメッセージのエクスペリエンスオプションを設定できます。また、iOS デバイスのペイロードオプションおよびカスタムオプションを含む、高度なオプションも設定できます。
keywords: モバイル
seo-description: 名前、メッセージテキストおよび宛先オプションを含む、プッシュメッセージおよびリッチプッシュメッセージのエクスペリエンスオプションを設定できます。また、iOS デバイスのペイロードオプションおよびカスタムオプションを含む、高度なオプションも設定できます。
seo-title: エクスペリエンスプッシュメッセージ
solution: Marketing Cloud、Analytics
title: エクスペリエンスプッシュメッセージ
topic: 指標
uuid: 1a8baf3e-9fea-452c- b0fc-4ba8ac270861
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: push message {#experience-push-message}

名前、メッセージテキストおよび宛先オプションを含む、プッシュメッセージおよびリッチプッシュメッセージのエクスペリエンスオプションを設定できます。また、iOS デバイスのペイロードオプションおよびカスタムオプションを含む、高度なオプションも設定できます。

1. 新しいプッシュメッセージのオーディエンスページで **[!UICONTROL 、「エクスペリエンス]**」をクリックします。

   ![エクスペリエンスプッシュメッセージ画面](assets/experience-push-message.png)

1. このメッセージの名前を入力します。
1. 次のフィールドの「**[!UICONTROL メッセージ]」セクションに情報を入力します。**

   * **[!UICONTROL コンテンツ]**

      メッセージのテキストを指定します。最大 140 文字を指定できます。

   * **[!UICONTROL メディア URL]**

      プッシュ通知メッセージで使用するメディアファイルの URL を入力します。高度なプッシュ通知を使用する要件については、以下の *「リッチプッシュ通知* の要件」を参照してください。

      >[!IMPORTANT]
      >
      >プッシュ通知で画像またはビデオを表示するには、次に留意してください。
      > * `attachment-url` データは、プッシュペイロードで処理されます。
      > * メディア URL は、リクエストのスパイクを処理できる必要があります。


   * **[!UICONTROL 送信先]**

      メッセージをクリックスルーしたら、ユーザーを送る特定の宛先（Web、ディープまたはハイブリッドリンク）を選択します。For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >When you use the * **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. 「**[!UICONTROL ディープリンク]」のみが追跡されます。**

## リッチプッシュ通知の要件

以下に、豊富なプッシュ通知を送信するための要件を示します。

* **サポートされているバージョン**

   以下のバージョンでは、リッチプッシュ通知がサポートされています。
   * Android 4.1.0 以降
   * iOS 10 以降

      >[!IMPORTANT]
      >
      >次の情報に留意してください。
      >* 以前のバージョンに送信されたリッチプッシュメッセージは送信されますが、テキストのみが表示されます。
      >* 現時点では、視聴のサポートはありません。


* **ファイル形式**

   次に、サポートされるファイル形式を示します。
   * 画像：JPG および PNG
   * アニメーション（iOS のみ）：GIF
   * ビデオ（iOS のみ）：MP4

* **URL形式**
   * HTTPS のみ

* **サイズ調整**
   * 画像は2:1形式でなければなりません。または、切り抜かれます。

リッチプッシュ通知の設定について詳しくは、次のコンテンツを参照してください。

* [Androidでプッシュ通知を受信する](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [iOSでのリッチプッシュ通知の受信](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

エクスペリエンスページでプッシュメッセージを設定するには:

1. (**Optional**) Click the **[!UICONTROL Show Advanced Options]** link to configure additional options:

   * **[!UICONTROL ペイロード：データ]**

      プッシュ通知またはローカル通知経由でアプリに送信される JSON 形式のカスタムプッシュペイロードを指定します。Android および iOS の上限は 4 KB です。

   * **[!UICONTROL Apple オプション：カテゴリ]**

      プッシュおよびローカル通知のカテゴリを指定します。詳しくは、*iOS Developer Library* の [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) を参照してください。

   * **[!UICONTROL Apple オプション：サウンド]**

      再生するアプリバンドルのサウンドファイルの名前を指定します。指定しない場合、デフォルトのアラートサウンドが再生されます。詳しくは、*iOS Developer Library* の [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) を参照してください。

   * **[!UICONTROL Apple オプション：利用可能なコンテンツ]**

      このオプションを選択して、メッセージが届くと、iOS はバックグラウンドでアプリを起動し、アプリがメッセージのペイロードに基づいてコードを実行できるようにします。For more information, see [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) in the *iOS Developer Library*.

1. （オプション）次のアイコンをクリックして、メッセージのレイアウトをプレビューします。

   * **[!UACROL x Summary}**

      プレビューペインを非表示にします。![プレビュー](assets/icon_preview.png) をクリックすると、プレビューペインが再び表示されます。

   * **[!UICONTROL 方向の変更]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). 腕時計の場合、丸い盤面から四角い盤面に向きが変わります。

   * **[!UICONTROL ユーザーの腕時計でのプレビュー]**

      ユーザーの視聴時にメッセージをプレビューするには、監視アイコンをクリック ![](assets/icon_watch.png)します。

   * **[!UICONTROL ユーザーの携帯電話でのプレビュー]**

      ユーザーの携帯電話アイコンに表示されるメッセージをプレビューするには、 ![「電話」アイコン](assets/icon_phone.png)をクリックします。

   * **[!UICONTROL ユーザーのタブレットでのプレビュー]**

      ユーザーのタブレットでメッセージをプレビューするには、タブレットアイコンをクリック ![](assets/icon_tablet.png)します。
   プレビューパネルの下部に、前の手順で選択したオーディエンスの説明を表示できます。

1. **（オプション**）「 **[!UICONTROL テスト」]** をクリックして、テスト目的で指定したデバイスにメッセージをプッシュします。
1. サービスを選択して、メッセージをプッシュする少なくとも 1 つのデバイスのプッシュトークンを入力します。

   複数のデバイスにメッセージをプッシュするには、コンマ区切りリストでトークンを指定します。

1. 設定スケジュールオプションを設定します。

   詳しくは [、「スケジュール」を参照してください。プッシュメッセージ](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)を参照してください。
