---
description: Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。
seo-description: Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。
seo-title: プッシュメッセージ
solution: Marketing Cloud、Analytics
title: プッシュメッセージ
topic: 開発者と導入
uuid: 729d4010-3733-4dff- b188- ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile および Adobe Mobile SDK を使用すると、ユーザーにプッシュメッセージを送信できます。SDK を使用して、プッシュメッセージをクリックした後にアプリを開いたユーザーを簡単にレポートすることもできます。

プッシュメッセージを使用するには、SDK バージョン 4.6 以降が&#x200B;**必要**&#x200B;です。

>[!IMPORTANT]
>
>アプリ内にExperience Cloud IDを手動で設定しないでください。手動で設定すると、新しい一意のユーザーが作成されます。このユーザーは、オプトインステータスが原因でプッシュメッセージを受信しません。例えば、プッシュメッセージを受信するためにオプトインしているユーザーがアプリにログインしたとします。ログイン後、アプリ内で ID を手動で設定すると、プッシュメッセージの受信をオプトインしていない新しい一意のユーザーが作成されます。この新しいユーザーは、プッシュメッセージを受信しません。
>
>アプリケーションを新しいレポートスイートに移動することはできません。新しいレポートスイートに移行すると、プッシュ設定が破損し、メッセージが送信されない可能性があります。

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>アプリが既にFireBase Cloud Messaging（FCM）経由でメッセージを使用するように設定されている場合、次の手順の一部が既に完了している可能性があります。

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   `"marketingCloud"` オブジェクトには、プッシュメッセージ用に設定された `"org"` プロパティが必要です。

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

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. `collectLifecycleData` メソッドでアクティビティを渡してレポートを有効にします。

   プッシュクリックスルーレポートを有効にするための要件を次に示します。

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. この方法は `putExtras` 、メソッドを使用して実行できます。For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * クリックスルーのターゲットアクティビティでは、`collectLifecycleData` 呼び出しでアクティビティを SDK に渡す必要があります。

      次の情報に留意してください。

      * 使用 `Config.collectLifecycleData(this)` また `Config.collectLifecycleData(this, contextData)`は

      * **** 使用 `Config.collectLifecycleData()`しないでください。



