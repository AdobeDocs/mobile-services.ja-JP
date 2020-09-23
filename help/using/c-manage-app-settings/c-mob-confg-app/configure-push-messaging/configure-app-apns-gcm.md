---
description: Apple Push Notification Service（APNS）または Firebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。
keywords: mobile
seo-description: Apple Push Notification Service（APNS）または Firebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。
seo-title: APNS または FCM を使用するアプリ設定
solution: Experience Cloud,Analytics
title: APNS または FCM を使用するアプリ設定
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 90%

---


# APNS または FCM を使用するアプリ設定{#configure-app-to-use-apns-or-fcm}

Apple Push Notification Service（APNS）または Firebase Cloud Messaging（FCM）を使用するようにアプリを設定できます。

## Android アプリ {#section_41D304102CDF4586911EC1413AD35A10}

### アプリで FCM が有効になっていない場合

このシナリオで FCM を使用するように Android アプリを設定するには：

1. [https://firebase.google.com/](https://firebase.google.com/) に移動し、Google デベロッパー資格情報を使用してログインします。

1. **[!UICONTROL 使ってみる]** をクリックし、**[!UICONTROL プロジェクトを追加]** を選択します。

1. プロジェクト名を入力します。Firebase 向け Google Analytics にオプトインする場合は、コントローラー間の利用条件に同意するチェックボックスをクリックします。

1. **[!UICONTROL プロジェクトを作成]** をクリックし、プロジェクトが作成されるまで待ちます。

1. 作成したプロジェクトをクリックすると、作成したプロジェクトの **[!UICONTROL プロジェクトの概要]** ページが表示されます。Android アイコンの付いたボタンをクリックして、Android アプリをプロジェクトに追加します。

1. 必要に応じて、アプリのパッケージ名、アプリのニックネームおよび署名証明書を入力します。

1. セットアップウィザードで提案された追加の手順に従います。Firebase サーバーとの通信をテストして Firebase の設定を確認した後、**[!UICONTROL プロジェクトの概要]** ページに戻ります。

1. **[!UICONTROL プロジェクトの概要]** ボタンの右にある歯車アイコンを右クリックし、**[!UICONTROL プロジェクトの設定]** をクリックします。

1. **[!UICONTROL クラウドメッセージング]** タブをクリックします。

1. 後で使用するために、**[!UICONTROL レガシーサーバーキー]** と **[!UICONTROL 送信者 ID]** をコピーします。

   以下に例を示します。

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### アプリで FCM が有効になっている場合

このシナリオで FCM を使用するように Android アプリを設定するには：

1. [https://firebase.google.com/](https://firebase.google.com/) に移動し、Google デベロッパー資格情報を使用してログインします。

1. **[!UICONTROL 使ってみる]** をクリックします。プロジェクトのインデックスページが開きます。Android アプリとリンクされている Firebase 対応プロジェクトを見つけ、プロジェクトカードをクリックします。

1. 次に、そのプロジェクトで **[!UICONTROL プロジェクトの概要]** を読み込む必要があります。**[!UICONTROL プロジェクトの概要]** ボタンの右にある歯車アイコンを右クリックし、**[!UICONTROL プロジェクトの設定]** をクリックします。

1. **[!UICONTROL クラウドメッセージング]** タブをクリックします。

1. 後で使用するために、**[!UICONTROL レガシーサーバーキー]** と **[!UICONTROL 送信者 ID]** をコピーします。

   以下に例を示します。

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS アプリ {#section_2031DAB485FC4D2B9027E42AD90B294D}

iOS アプリで APNS を使用するように設定するには：

1. Go to [https://developer.apple.com/account](https://developer.apple.com/account) and log in to your [Apple Developer account](https://developer.apple.com/account).
1. **[!UICONTROL iOS Apps]** で、**[!UICONTROL Identifiers]** を選択します。
1. 既にプッシュ用のアプリ ID がある場合は、手順 11 に進みます。
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 「アプリIDの説明」を入力します。
1. 「アプリIDサフィックス」を入力します。

   >[!IMPORTANT]
   >
   >プッシュをサポートするには、ワイルドカードを&#x200B;**使用していない**&#x200B;明示的なアプリ ID（例：`- com.tester.pushSample`）を使用する必要があります。

1. **[!UICONTROL アプリサービス]** で、**[!UICONTROL プッシュ通知]** のチェックボックスを選択します。
1. **[!UICONTROL 続行]** をクリックします。
1. **[!UICONTROL 送信]** をクリックします。
1. **[!UICONTROL 完了]** をクリックします。
1. リストからプッシュメッセージを使用するように設定されているアプリ ID を選択し、**[!UICONTROL 編集]** をクリックします。
1. 既にプッシュ証明書を持っている場合は、手順 15 にスキップします。
1. 下の **[!UICONTROL プッシュ通知]** までスクロールし、適切な **[!UICONTROL 証明書を作成...]** ボタンをクリックします。

   クリックするボタンは、開発用と実稼働用のどちらの証明書を作成するかによって異なります。
1. Apple の Web サイトで CSR を作成し、CSR をアップロードして証明書を生成する手順に従います。
1. 下の **[!UICONTROL プッシュ通知]** セクションまでスクロールし、先ほど作成した SSL 証明書をダウンロードします。
1. ダウンロードした証明書をダブルクリックして、キーチェーンに追加します。

### SSL 証明書および秘密鍵

SSL 証明書および秘密鍵を取得するには（APNS）：

1. **[!UICONTROL キーチェーンアクセス]**&#x200B;を開きます。
1. **[!UICONTROL 証明書]** をクリックし、アプリおよび環境に適した&#x200B;**[!UICONTROL iOS プッシュサービス証明書]**&#x200B;を確認します。

   バンドルIDを照合し、開発用か実稼働用かを判断することで、正しい証明書を特定できます。

1. 証明書を展開し、秘密鍵が含まれていることを確認します。
1. 秘密鍵を右クリックし、**[!UICONTROL の書き出し&#x200B;*`<name of key>`*]**をクリックします。
1. ダイアログボックスに必要な情報を入力し、新しい `.p12` ファイルを保存します。

   パスワードを入力する必要はありません。

1. **[!UICONTROL 秘密鍵]** に、`.p12` ファイルを入力します。

