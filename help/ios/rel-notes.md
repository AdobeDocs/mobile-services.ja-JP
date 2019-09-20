---
description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Marketing Cloud ,Analytics
title: リリースノート
topic: 開発者と導入
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# リリースノート {#release-notes}

Experience cloudソリューション用iOS SDK 4.xのリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019年9月21日：バージョン4.18.8**

* アプリ内メッセージ：

   * iOS 10以降を実行するデバイスでは、フレームワークを使用し `UserNotifications` て、リンクされたアプリに対するローカル通知のスケジュールを設定できるようになりまし `UserNotifications.framework`た。
   * フルスクリーンメッセージで、Xcodeプロジェクト内でリ `WebKit.framework`ンクする必要がある、WKWebViewsを使用するようになりました。
   * プッシュクリックスルーペイロードをアプリ内メッセージの特徴として使用できなかったバグを修正しました。
   * クラッシュの問題を修正しました。

* 一般 — Analyticsの呼び出しのたびに、SDKデータがペアのwatchOSアプリと同期されるバグを修正しました。

**2019年8月2日：バージョン4.18.7**

* バージョン4.18.6で導入された変更を元に戻しました。一部の環境では、11.0より前のiOSバージョンを実行しているデバイスでクラッシュが発生していました。

* Adobe Target:にプロパティ `requestLocationParameters` が追加され、イ `ADBTargetRequestObject`ンプレッションIDをTargetのリクエストと共に送信できるようになりました。

**2019年7月19日：バージョン4.18.6**

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび `sessionId` が含まれるようになりました。
* Adobe Target：メモリリークを修正しました。
* 訪問者 ID サービス：`visitorAppendToURL` および `visitorGetUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019年6月6日：バージョン4.18.5**

* Analytics — プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

**2019年5月25日：バージョン4.18.4**

* 訪問者IDサービス —
   `visitorGetUrlVariablesAsync` APIを30秒に設定します。

* 訪問者IDサービス — `setPushIdentifier` API呼び出しは、呼び出されるたびに訪問者IDサービスに同期呼び出しを送信するようになりました。

すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)を参照してください。
