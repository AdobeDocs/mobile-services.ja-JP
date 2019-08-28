---
description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x のリリースノートと既知の問題です。
seo-title: リリースノート
solution: Marketing Cloud ,Analytics
title: リリースノート
topic: 開発者と導入
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# リリースノート {#release-notes}

Experience Cloudソリューション用のiOS SDK4. xのリリースノート、既知の問題およびホットフィックス情報を次に示します。

**2019年8月2日:バージョン4.18.7**

* バージョン4.18.6で導入された変更を元に戻しました。一部の環境では、iOSバージョン11.0より古いiOSでクラッシュが発生していました。

* Adobe Target:プロパティが `requestLocationParameters` 追加され、 `ADBTargetRequestObject`Targetリクエストと共にimageIdを送信できるようになりました。

**2019年7月18日:バージョン4.18.6**

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび `sessionId` が含まれるようになりました。
* Adobe Target：メモリリークを修正しました。
* 訪問者 ID サービス：`visitorAppendToURL` および `visitorGetUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。 

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

**2019年6月6日:バージョン4.18.5**

* Analytics-プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

**2019年5月24日:バージョン4.18.4**

* 訪問者IDサービス-
   `visitorGetUrlVariablesAsync` APIを30秒から30秒に設定します。

* 訪問者IDサービス- `setPushIdentifier` API呼び出しが呼び出されるたびに、訪問者IDサービスへの同期呼び出しが送信されるようになりました。

すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)を参照してください。
