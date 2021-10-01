---
description: Apple の通知に画像ファイルを添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知に対するユーザーのエンゲージメントが大幅に向上する可能性があります。
title: リッチプッシュ通知の受信
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 39%

---

# リッチプッシュ通知の受信 {#receive-rich-push-notifications}

Apple の通知に画像ファイルを添付できます。 ビジュアルコンポーネントを追加すると、プッシュ通知に対するユーザーのエンゲージメントが大幅に向上する可能性があります。

iOS アプリでリッチプッシュ通知を受信するには：

1. アプリにプッシュメッセージを実装するため、[プッシュメッセージ](/help/ios/messaging-main/push-messaging/push-messaging.md)の手順を完了します。
1. テキストのプッシュメッセージをアプリに送信できることを確認します。
1. 次の手順を実行して、通知サービス拡張を追加します。

   1. Xcode プロジェクトで、**[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]** を選択します。
   1. **[!UICONTROL Notification Service Extension]** を選択します。
   1. `NotificationService.m` ファイルが存在することを確認します。

1. `NotificationService.m` ファイルを開き、以下の Delegate メソッドが存在することを確認します。

   * 通知リクエストを受け取る 1 つのメソッド。
   * サービス拡張の有効期限を処理する 1 つのメソッド。

      リッチプッシュ通知を受信するには、最初のメソッドを使用します。

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


iOS を使用したリッチプッシュ通知について詳しくは、[UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment) を参照してください。
