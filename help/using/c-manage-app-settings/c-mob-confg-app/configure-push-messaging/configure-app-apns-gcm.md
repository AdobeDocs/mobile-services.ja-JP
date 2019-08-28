---
description: Apple Push Notification Service（APNS）またはFirebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。
keywords: モバイル
seo-description: Apple Push Notification Service（APNS）またはFirebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。
seo-title: APNSまたはFCMを使用するようにアプリを設定する
solution: Marketing Cloud、Analytics
title: APNSまたはFCMを使用するようにアプリを設定する
topic: 指標
uuid: fa411f2a- ba47-4499- bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# APNSまたはFCMを使用するようにアプリを設定する{#configure-app-to-use-apns-or-fcm}

Apple Push Notification Service（APNS）またはFirebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。

## Android アプリ {#section_41D304102CDF4586911EC1413AD35A10}

### アプリケーションでFCMが有効になっていない場合

このシナリオでFCMを使用するようにAndroidアプリを設定するには:

1. [https://firebase.google.com/にアクセス](https://firebase.google.com/) し、Googleデベロッパー資格情報を使用してログインします。

1. 「 **[!UICONTROL 開始」]** をクリックし、「プロジェクト **[!UICONTROL を追加」を選択]**&#x200B;します。

1. プロジェクト名を入力し、FirebaseデータのGoogle Analyticsにオプトインする場合は、コントローラーコントローラーの用語を受け入れるチェックボックスをクリックします。

1. 「 **[!UICONTROL プロジェクトを作成」]** をクリックし、プロジェクトが作成されるまで待ちます。

1. 作成したプロジェクトをクリックし、作成したプロジェクトの **[!UICONTROL プロジェクト概要]** ページを表示します。Androidアイコンを使用してボタンをクリックすると、Androidアプリがプロジェクトに追加されます。

1. 必要に応じて、アプリパッケージ名、アプリケーションのニックネームおよび署名証明書を入力します。

1. セットアップウィザードで推奨される追加手順に従います。Firebaseサーバーとの通信をテストしてFirebaseセットアップを確認したら **[!UICONTROL 、プロジェクト概要]** ページに戻ります。

1. **[!UICONTROL プロジェクトの概要]** ボタンの右にある歯車アイコンをクリックし、 **[!UICONTROL 「プロジェクト設定]**」をクリックします。

1. **[!UICONTROL "Cloud Messaging"]** タブをクリックします。

1. **[!UICONTROL レガシーサーバーキー]** および **[!UICONTROL Sender ID]** をコピーして、後で使用します。

   以下に例を示します。

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### アプリケーションでFCMが有効になっている場合

このシナリオでFCMを使用するようにAndroidアプリを設定するには:

1. [https://firebase.google.com/にアクセス](https://firebase.google.com/) し、Googleデベロッパー資格情報を使用してログインします。

1. 「開始」をクリック ****&#x200B;します。これにより、プロジェクトのインデックスページが開きます。AndroidアプリにリンクされているFirebase有効プロジェクトを見つけて、プロジェクトカードをクリックします。

1. プロジェクトの **[!UICONTROL プロジェクト概要]** が読み込まれます。**[!UICONTROL プロジェクトの概要]** ボタンの右にある歯車アイコンをクリックし、 **[!UICONTROL 「プロジェクト設定]**」をクリックします。

1. **[!UICONTROL "Cloud Messaging"]** タブをクリックします。

1. **[!UICONTROL レガシーサーバーキー]** および **[!UICONTROL Sender ID]** をコピーして、後で使用します。

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
1. **[!UICONTROL "iOSアプリ]**»で、??«識別子??****
1. プッシュ用にアプリIDを設定している場合は、手順11に進みます。
1. **[!UICONTROL "+]** 」ボタンを押して、新しいアプリIDを作成します。
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

   クリックするボタンは、開発版または本番環境用の証明書を作成しているかどうかによって異なります。
1. AppleのWebサイトでCSRを作成し、CSRをアップロードして証明書を生成する手順について説明します。
1. 下の「**[!UICONTROL プッシュ通知]**」セクションまでスクロールし、先ほど作成した SSL 証明書をダウンロードします。
1. ダウンロードした証明書をダブルクリックして、キーチェーンに追加します。

### SSL証明書および秘密鍵

SSL証明書および秘密鍵（APNS）を取得するには:

1. **[!UICONTROL キーチェーンアクセス]**&#x200B;を開きます。
1. **[!UICONTROL 「マイ証明書]** 」をクリックし、アプリケーションおよび環境の適切 **[!UICONTROL なiOSプッシュサービス証明書]** を見つけます。

   バンドル ID を照合し、開発用か実稼動用かを確認することで、適切な証明書を見つけることができます。

1. 証明書を展開し、秘密鍵が含まれていることを確認します。
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. ダイアログボックスに必要な情報を入力し、新しい `.p12` ファイルを保存します。

   パスワードを入力する必要はありません。

1. **[!UICONTROL 「秘密鍵]**」にファイルを `.p12` 入力します。

