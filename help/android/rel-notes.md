---
description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Marketing Cloud ,Analytics
title: リリースノート
topic: 開発者と導入
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# リリースノート {#release-notes}

Experience cloudソリューション用Android SDK 4.xのリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019年9月21日：バージョン4.17.10**

* 一般：Android APIレベル21以降の一部の地域でのロケール文字列の生成を修正しました。

**2019年7月19日：バージョン4.17.8**

* Adobe Target:すべてのリクエストに、URLクエリパラメーターにclientとsessionIdが含まれるようになりました。
* アプリ内メッセージ：空のクリックスルー URL でメッセージがトリガーされた場合に Android アプリがクラッシュする問題を修正しました。
* 訪問者 ID サービス：`Visitor.appendToURL` および `Visitor.getUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019年6月7日：バージョン4.17.7**

* 一般 — 20未満のAndroid APIレベルでのネットワーク呼び出しで、TLS 1.1またはTLS 1.2が使用されるようになりました。
* 解析 — プッシュ通知が有効な場合に、プッシュオプトインステータスがライフサイクルデータに追加されました。

**2019年5月25日：バージョン4.17.6**

* 訪問者IDサービス —
   `setPushIdentifier` API呼び出しは、呼び出されるたびに訪問者IDサービスに非同期呼び出しを送信するようになりました。

* 訪問者IDサービス — 接続と読み取りのタイムアウトを2秒から5秒に増やしました。


すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)を参照してください。
