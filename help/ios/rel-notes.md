---
description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Experience Cloud,Analytics
title: リリースノート
topic: 開発者と導入
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# リリースノート {#release-notes}

Experience Cloud ソリューション用 iOS SDK 4.x のリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019 年 9 月 21 日：バージョン 4.18.8**

* アプリ内メッセージ：

   * iOS 10 以降を実行するデバイスでは、`UserNotifications` フレームワークを使用して、`UserNotifications.framework` にリンクされたアプリに対するローカル通知のスケジュールを設定できるようになりました。
   * フルスクリーンメッセージで、Xcode プロジェクト内でリンクする必要がある、`WebKit.framework` の WKWebViews を使用するようになりました。
   * プッシュのクリックスルーペイロードをアプリ内メッセージの特性として使用できなかったバグを修正しました。
   * クラッシュの問題を修正しました。

* 一般 - Analytics の呼び出しごとに SDK データがペアリングされた WatchOS アプリに同期されるバグを修正しました。

**2019 年 8 月 3 日：バージョン 4.18.7**

* バージョン 4.18.6 で導入された変更を元に戻しました。一部の環境において、11.0 より前の iOS バージョンを実行しているデバイスでクラッシュが発生していました。

* Adobe Target：`ADBTargetRequestObject` のプロパティ `requestLocationParameters` が追加され、インプレッション ID を Target のリクエストと共に送信できるようになりました。

**2019 年 7 月 19 日：バージョン 4.18.6**

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび `sessionId` が含まれるようになりました。
* Adobe Target：メモリリークを修正しました。
* 訪問者 ID サービス：`visitorAppendToURL` および `visitorGetUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019 年 6 月 6 日：バージョン 4.18.5**

* Analytics - プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

**2019 年 5 月 25 日：バージョン 4.18.5**

* 訪問者 ID サービス - 
   `visitorGetUrlVariablesAsync` API の戻りタイムアウトを 30 秒に増やしました。

* 訪問者 ID サービス — `setPushIdentifier` API I呼び出しは、呼び出されるたびに同期呼び出しを訪問者IDサービスへと送信するようになりました。

すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/ja_JP/whatsnew/)を参照してください。
