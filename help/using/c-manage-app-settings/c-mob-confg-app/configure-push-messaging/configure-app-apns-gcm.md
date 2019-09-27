---
description: Apple Push Notification Service(APNS)またはFirebase Cloud Messaging(FCM)を使用するようにアプリを設定できます。
keywords: モバイル
seo-description: Apple Push Notification Service(APNS)またはFirebase Cloud Messaging(FCM)を使用するようにアプリを設定できます。
seo-title: APNSまたはFCMを使用するためのアプリの設定
solution: Marketing Cloud,Analytics
title: Configure App to use APNS or FCM
topic: 指標
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# APNSまたはFCMを使用するようにアプリを設定する{#configure-app-to-use-apns-or-fcm}

Apple Push Notification Service(APNS)またはFirebase Cloud Messaging(FCM)を使用するようにアプリを設定できます。

## Android アプリ {#section_41D304102CDF4586911EC1413AD35A10}

### アプリでFCMが有効になっていない場合

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 「はじめに **[!UICONTROL 」をクリックし、「プロジ]** ェクトを追加 ****」を選択します。

1. プロジェクト名を入力し、Firebaseデータ用にGoogle Analyticsにオプトインする場合は、コントローラーコントローラーの条件に同意するチェックボックスをクリックします。

1. Click Create project and wait for the project to be created.****

1. Click on the created project and the Project Overview page for the created project should be shown. **** Click the button with the Android icon to add an Android app to the project.

1. Enter the app package name, app nickname, and signing certificate if needed.

1. Follow the additional steps suggested by the setup wizard. After verifying the Firebase setup by testing communication with the Firebase servers, return to the Project Overview page.****

1. Click the gear icon to the right of the Project Overview button and click Project Settings.********

1. 「 **[!UICONTROL Cloud Messaging]** 」タブをクリックします。

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   以下に例を示します。

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### アプリでFCMが有効になっている場合

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 「はじ **[!UICONTROL めに]**」をクリック This will open the project index page. Find the Firebase enabled project which is linked to your Android app and click the project card.

1. 次に、プ **[!UICONTROL ロジェクトのプロジェクト概要]** (Project Overview)を読み込みます。 「プロジェクトの概要」ボタンの右にある歯車アイコンをク **[!UICONTROL リックし、]** 「プロジェクト設定」を **[!UICONTROL クリックします]**。

1. 「 **[!UICONTROL Cloud Messaging]** 」タブをクリックします。

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   以下に例を示します。

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

iOS アプリで APNS を使用するように設定するには：

1. [https://developer.apple.com/account](https://developer.apple.com/account) に移動して、[Apple Developer アカウント](https://developer.apple.com/account)にログインします。
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. プッシュ用にアプリIDが設定されている場合は、手順11に進みます。
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 「App ID Description」を入力します。
1. 「App ID Suffix」を入力します。

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. 「**[!UICONTROL アプリサービス]**」で、「**[!UICONTROL プッシュ通知]**」のチェックボックスを選択します。
1. Click **[!UICONTROL Continue]**.
1. Click **[!UICONTROL Submit]**.
1. 「**[!UICONTROL 完了]**」をクリックします。
1. リストからプッシュメッセージを使用するように設定されているアプリ ID を選択し、「**[!UICONTROL 編集]**」をクリックします。
1. 既にプッシュ証明書を持っている場合は、手順 15 にスキップします。
1. 下の「**[!UICONTROL プッシュ通知]**」までスクロールし、適切な「**[!UICONTROL 証明書を作成...]**」ボタンをクリックします。

   クリックするボタンは、開発用の証明書を作成しているか実稼働用の証明書を作成しているかによって異なります。
1. AppleのWebサイトでCSRを作成し、CSRをアップロードして、証明書を生成する手順に従います。
1. 下の「**[!UICONTROL プッシュ通知]**」セクションまでスクロールし、先ほど作成した SSL 証明書をダウンロードします。
1. ダウンロードした証明書をダブルクリックして、キーチェーンに追加します。

### SSL証明書と秘密鍵

SSL証明書と秘密鍵(APNS)を取得するには：

1. **[!UICONTROL キーチェーンアクセス]**&#x200B;を開きます。
1. Click **[!UICONTROL My Certificates]** and find the appropriate **[!UICONTROL iOS Push Services Certificate]** for your app and environment.

   バンドル ID を照合し、開発用か実稼動用かを確認することで、適切な証明書を見つけることができます。

1. 証明書を展開し、秘密鍵が含まれていることを確認します。
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. ダイアログボックスに必要な情報を入力し、新しいファイルを保存 `.p12` します。

   パスワードを入力する必要はありません。

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

