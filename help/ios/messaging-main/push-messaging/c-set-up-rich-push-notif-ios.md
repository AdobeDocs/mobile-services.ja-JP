---
description: 画像ファイルを Apple の通知に添付することができます。視覚的なコンポーネントを追加することによって、ユーザーのプッシュ通知とのエンゲージメントを大幅に向上させることができます。
seo-description: 画像ファイルを Apple の通知に添付することができます。視覚的なコンポーネントを追加することによって、ユーザーのプッシュ通知とのエンゲージメントを大幅に向上させることができます。
seo-title: リッチプッシュ通知の受信
title: リッチプッシュ通知の受信
uuid: 0dbda409- cf49-4eb8-90ee- baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

画像ファイルを Apple の通知に添付することができます。視覚的なコンポーネントを追加することによって、ユーザーのプッシュ通知とのエンゲージメントを大幅に向上させることができます。

リッチプッシュ通知を iOS アプリで受信するには：

1. アプリのプッシュメッセージを実装するには、 [プッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. テキストのプッシュメッセージをアプリに送信できることを確認します。
1. 以下の手順を実行して、Notification Service Extension を追加します。

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. **[!UICONTROL 「通知サービス拡張]**」を選択します。
   1. `NotificationService.m` ファイルが存在することを確認します。

1. `NotificationService.m` ファイルを開き、以下の Delegate メソッドが存在することを確認します。

   * 通知リクエストを受信する 1 つのメソッド。
   * サービスエクステンションの有効期限を扱う 1 つのメソッド。

      リッチプッシュ通知を受信するには、最初のメソッドを使用します。

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      この方法では、キーを `userInfo``attachment-url` 使用してメディアURLを取得できます。ローカルディレクトリにファイルをダウンロードした後、ローカルパスを追加 `bestAttemptContent.attachments`します。

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


iOS を使用したリッチプッシュ通知について詳しくは、[UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment) を参照してください。
