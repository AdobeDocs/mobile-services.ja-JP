---
description: 画像ファイルをAppleの通知に添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に増加する可能性があります。
seo-description: 画像ファイルをAppleの通知に添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に増加する可能性があります。
seo-title: リッチプッシュ通知の受信
title: リッチプッシュ通知の受信
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 35%

---


# リッチプッシュ通知の受信{#receive-rich-push-notifications}

画像ファイルをAppleの通知に添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知を使用したユーザーの関与が大幅に増加する可能性があります。

iOSアプリでリッチプッシュ通知を受信するには：

1. アプリにプッシュメッセージを実装するため、[プッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)の手順を完了します。
1. テキストのプッシュメッセージをアプリに送信できることを確認します。
1. Notification Service追加の拡張機能を使用するには、次の手順を実行します。

   1. In your Xcode project, select  **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. **[!UICONTROL Notification Service Extension]** を選択します。
   1. `NotificationService.m` ファイルが存在することを確認します。

1. `NotificationService.m` ファイルを開き、以下の Delegate メソッドが存在することを確認します。

   * 通知要求を受け取る1つのメソッド。
   * サービス拡張の有効期限を処理する1つのメソッド。

      リッチプッシュ通知を受信するには、最初の方法を使用します。

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      この方法では、`attachment-url` キーを使用して `userInfo` からメディア URL を取得できます。ファイルをローカルディレクトリにダウンロードした後、`bestAttemptContent.attachments` にローカルパスを追加します。

      このメソッドのコード例を以下に示します。

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
