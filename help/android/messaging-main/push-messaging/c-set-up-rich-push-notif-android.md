---
description: Android通知には、画像ファイルを添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に向上する可能性があります。
seo-description: Android通知には、画像ファイルを添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に向上する可能性があります。
seo-title: リッチプッシュ通知の受信
title: リッチプッシュ通知の受信
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 60%

---


# リッチプッシュ通知の受信{#receive-rich-push-notifications}

Android通知には、画像ファイルを添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に向上する可能性があります。

## 受信リッチプッシュメッセージ（GCM）の処理{#section_AF1A3BC2312C4E1DA517CC90296C11E2}

アプリがフォアグラウンドにある場合、プッシュメッセージは `FirebaseMessagingService` クラスを拡張するアプリによって処理されます。このクラスは、マニフェストファイルで次のように宣言します。

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>`onMessageReceived()` 実装を含むクラスは、受信したデータを処理します。

プッシュメッセージにメディア URL が含まれている場合、URL は `onMessageReceived()` 関数に渡される `RemoteMessage` パラメーターで利用できます。使用するキーは、次のコードサンプルに示すように、`attachment-url` です。

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>`NotificationCompat.BigPictureStyle` を設定すると、大きな画像が表示されない場合があります。大きな画像を常に表示するには、ネイティブの `Notification.BigPictureStyle` を設定してください。

## サンプルのリッチプッシュ通知 {#section_6819316BEDDE45108413B541CA2BB2DC}

画像を含むリッチプッシュ通知の例を次に示します。

![](assets/rich-push-notification_example.png)

For more information about rich push notifications with Android, see [Engage with Rich Notifications](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
