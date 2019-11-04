---
description: Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。
seo-description: Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。
seo-title: プッシュメッセージ
solution: Experience Cloud,Analytics
title: プッシュメッセージ
topic: 開発者と導入
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# プッシュメッセージ{#push-messaging}

Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。

プッシュメッセージを使用するには、SDK バージョン 4.6 以降が&#x200B;**必要**&#x200B;です。

>[!IMPORTANT]
>
>アプリ内部の Experience Cloud ID を手動で設定しないでください。手動で設定すると、新しい一意のユーザーが作成されます。このユーザーは、オプトインステータスが原因でプッシュメッセージを受信しません。例えば、プッシュメッセージを受信するためにオプトインしているユーザーがアプリにログインしたとします。ログイン後、アプリ内で ID を手動で設定すると、プッシュメッセージの受信をオプトインしていない新しい一意のユーザーが作成されます。この新しいユーザーは、プッシュメッセージを受信しません。
>
>新しいレポートスイートへのアプリの移行はサポートされていません。新しいレポートスイートに移行すると、プッシュ設定が破損し、メッセージが送信されない可能性があります。

## プッシュメッセージの有効化 {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Google Cloud Messaging（FSM）経由でメッセージを使用するようアプリを既に設定している場合、次の手順の一部が既に完了していることがあります。

1. プッシュメッセージに必要な設定が `ADBMobileConfig.json` ファイルに含まれていることを確認します。

   `"marketingCloud"` オブジェクトの `"org"` プロパティをプッシュメッセージ用に設定する必要があります。

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. FireBase Cloud Messaging（FCM）API を使用して、登録 ID／トークンを取得します。

   * FCM の設定について詳しくは、[Android に Firebase Cloud Messaging クライアントアプリを設定する](https://firebase.google.com/docs/cloud-messaging/android/client)を参照してください。
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. 登録 ID／トークンは、`Config.setPushIdentifier(final String registrationId)` メソッドを使用して SDK に渡す必要があります。

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. `collectLifecycleData` メソッドでアクティビティを渡してレポートを有効にします。

   プッシュクリックスルーレポートを有効にするための要件を次に示します。

   * `FireBaseMessageService` の実装で、（RemoteMessage オブジェクトで `onMessageReceived` メソッドに渡される）メッセージデータが含まれたバンドルオブジェクトを、クリックスルーでターゲットアクティビティを開くために使用されるインテントに追加する必要があります。これには、`putExtras` メソッドを使用します。詳しくは、「[putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))」を参照してください。
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * クリックスルーのターゲットアクティビティでは、`collectLifecycleData` 呼び出しでアクティビティを SDK に渡す必要があります。

      次の情報に留意してください。

      * `Config.collectLifecycleData(this)` または `Config.collectLifecycleData(this, contextData)` を使用する。

      * `Config.collectLifecycleData()` は使用&#x2