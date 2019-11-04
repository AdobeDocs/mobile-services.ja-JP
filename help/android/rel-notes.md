---
description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Experience Cloud,Analytics
title: リリースノート
topic: 開発者と導入
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# リリースノート {#release-notes}

Experience Cloud ソリューション用 Android SDK 4.x のリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019 年 9 月 21 日：バージョン 4.17.10**

* 全般：Android API レベル 21 以降における、一部の地域のロケール文字列の生成を修正しました。

**2019 年 7 月 19 日：バージョン 4.17.8**

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび sessionId が含まれるようになりました。
* アプリ内メッセージ：空のクリックスルー URL でメッセージがトリガーされた場合に Android アプリがクラッシュする問題を修正しました。
* 訪問者 ID サービス：`Visitor.appendToURL` および `Visitor.getUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019 年 6 月 6 日：バージョン 4.17.7**

* 全般 - Android API のレベル 20 未満でのネットワーク呼び出しで、TLS 1.1 または TLS 1.2 が使用されるようになりました。
* Analytics - プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

**2019 年 5 月 24 日：バージョン 4.17.6**

* 訪問者 ID サービス - 
   `setPushIdentifier` API I呼び出しは、呼び出されるたびに同期呼び出しを訪問者IDサービスへと送信するようになりました。

* 訪問者 ID サービス - 接続と読み取りのタイムアウトを 2 秒から 5 秒に増やしました。


すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/ja_JP/whatsnew/)を参照してください。
