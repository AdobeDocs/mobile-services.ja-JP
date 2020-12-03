---
description: Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの adb_deeplink キーに含まれます。
seo-description: Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの adb_deeplink キーに含まれます。
seo-title: ディープリンクを使用したプッシュメッセージの実装
title: ディープリンクを使用したプッシュメッセージの実装
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 75%

---


# ディープリンクを使用したプッシュメッセージの実装{#implement-push-messaging-with-deep-linking}

Adobe Mobile Services UI で設定したディープリンク URL は、プッシュペイロードの adb_deeplink キーに含まれます。

URL は、`FirebaseMessagingService` の `remoteMessage.getData().get("adb_deeplink")` を呼び出すことで取得できます。

>[!TIP]
>
>ペイロードにディープリンク URL が含まれているかどうかに応じて、異なるインテントを定義できます。

1. 次のどちらかのタスクを実行します。

   * ディープリンク URL がプッシュペイロードに&#x200B;**含まれている**&#x200B;場合、その URL で `ACTION_VIEW` インテントを作成します。

      ユーザーがプッシュメッセージをクリックすると、ディープリンクがトリガーされます。

   * ディープリンクURL **がプッシュペイロードに含まれていない場合** 、アクティビティの1つを開くインテントを作成します。

## 例

`FirebaseMessagingService` から拡張されるクラスの実装例を示します。

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
