---
description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Marketing Cloud ,Analytics
title: リリースノート
topic: 開発者と導入
uuid: 16bb4de8- a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# リリースノート {#release-notes}

Experience Cloudソリューション用のAndroid SDK4. xのリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019年8月2日:バージョン4.17.9**

* 訪問者IDサービス:SyncIdentifiersの呼び出し時 `StrictMode` に違反を修正。

   この違反は、メインスレッドの共有環境設定を読み取ることによって発生していました。

* Adobe Target:属性が `requestLocationParameters` 追加され、 `TargetRequestObject`Targetリクエストと共にimageIdを送信できるようになりました。

**2019年7月18日:バージョン4.17.8**

* Adobe Target:すべてのリクエストに、URLクエリパラメーターにクライアントとsessionIdが含まれるようになりました。
* アプリ内メッセージ：空のクリックスルー URL でメッセージがトリガーされた場合に Android アプリがクラッシュする問題を修正しました。
* 訪問者 ID サービス：`Visitor.appendToURL` および `Visitor.getUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019年6月6日:バージョン4.17.7**

* 一般- Android APIレベルのネットワーキング呼び出しが、TLS1.1またはTLS1.2を使用するようになりました。
* Analytics-プッシュ通知が有効になっているときに、ライフサイクルデータにプッシュオプトインステータスを付加します。

**2019年5月24日:バージョン4.17.6**

* 訪問者IDサービス-
   `setPushIdentifier` API呼び出しで、呼び出されるたびに訪問者IDサービスへの同期呼び出しが送信されるようになりました。

* 訪問者IDサービス-接続を拡張し、タイムアウトを2秒から5秒に読み取りました。


すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)を参照してください。
