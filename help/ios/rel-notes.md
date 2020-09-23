---
description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートおよび既知の問題です。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートおよび既知の問題です。
seo-title: リリースノート
solution: Experience Cloud,Analytics
title: リリースノート
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---


# リリースノート {#release-notes}

Experience Cloud ソリューション用 iOS SDK 4.x のリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2020 年 7 月 16 日：バージョン 4.19.3**

* 一般：複数の等号ログインクエリパラメーターを含むディープリンク URL が正しく処理されない問題を修正しました。

**2020 年 3 月 25 日：バージョン 4.19.2**

* 一般：Target コードの漏れを修正しました。

**2020 年 3 月 13 日：バージョン 4.19.1**

* 一般：コール追跡のコンテキストデータに Swift Enum が含まれる場合に、クラッシュが発生する可能性があったを解決しました。
* Target：Target セッション ID は、Adobe Analytics に送信される Target 用内部 Analytics ヒットで、コンテキストデータパラメーター「a.target.sessionId」として追加されるようになりました。

**2020 年 2 月 5 日：バージョン 4.19.0**

* ライフサイクル：一部の古い iOS デバイスで報告されたセッション長の異常データを軽減するために、新しい API、pauseCollectingLifecycleData が追加されました。

**2019 年 11 月 9 日：バージョン 4.18.9**

* アプリ内メッセージ：キャッシュされた画像またはバンドルされた画像をフルスクリーンメッセージに読み込めなかったバグを修正しました。

**2019 年 9 月 21 日：バージョン 4.18.8**

* アプリ内メッセージ：

   * iOS 10 以降を実行するデバイスでは、`UserNotifications` フレームワークを使用して、`UserNotifications.framework` にリンクされたアプリに対するローカル通知のスケジュールを設定できるようになりました。
   * フルスクリーンメッセージで、Xcode プロジェクト内でリンクする必要がある、`WebKit.framework` の WKWebViews を使用するようになりました。
   * プッシュのクリックスルーペイロードをアプリ内メッセージの特性として使用できなかったバグを修正しました。
   * クラッシュの問題を修正しました。

* 一般：Analytics の呼び出しごとに SDK データがペアリングされた WatchOS アプリに同期されるバグを修正しました。

**2019 年 8 月 3 日：バージョン 4.18.7**

* バージョン 4.18.6 で導入された変更を元に戻しました。一部の環境において、11.0 より前の iOS バージョンを実行しているデバイスでクラッシュが発生していました。

* Adobe Target：`ADBTargetRequestObject` のプロパティ `requestLocationParameters` が追加され、インプレッション ID を Target のリクエストと共に送信できるようになりました。

**2019 年 7 月 19 日：バージョン 4.18.6**

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび `sessionId` が含まれるようになりました。
* Adobe Target：メモリリークを修正しました。
* 訪問者 ID サービス：`visitorAppendToURL` および `visitorGetUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019 年 6 月 6 日：バージョン 4.18.5**

* Analytics：プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

**2019 年 5 月 25 日：バージョン 4.18.5**

* 訪問者 ID サービス：
   `visitorGetUrlVariablesAsync` API の戻りタイムアウトを 30 秒に増やしました。

* 訪問者 ID サービス：`setPushIdentifier` API 呼び出しは、呼び出されるたびに同期呼び出しを訪問者 ID サービスへと送信するようになりました。

すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://docs.adobe.com/content/help/ja-JP/release-notes/experience-cloud/current.html)を参照してください。
