---
description: Experience Cloud ソリューション用 Android SDK 4.x のリリースノートと既知の問題です。
solution: Experience Cloud,Analytics
title: リリースノート
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 72%

---

# リリースノート {#release-notes}

Experience Cloud ソリューション用 Android SDK 4.x のリリースノート、既知の問題およびホットフィックス情報を次に示します。

## 2020 年 4 月 4 日：4.18.2

* アプリ内メッセージ：セキュリティ上の理由から、SDK で作成された WebViews で、プロパティ `setAllowFileAccess` が `false` に設定されるようになりました。

## 2020 年 3 月 13 日：4.18.1

* Target:Target セッション ID が、Adobe Analyticsに送信される内部 Analytics-for-Target ヒットで、コンテキストデータパラメーター `a.target.sessionId` として追加されるようになりました。

## 2020 年 1 月 17 日：4.18.0

* 獲得 - Google Play インストールリファラー API をサポートするため、新しい API である `Analytics.processGooglePlayInstallReferrerUrl(final String url)` を追加しました。

   リファラー API のインストールについて詳しくは、「[まだ InstallBroadcast を使用している場合は、2020 年 3 月 1 日までに再生リファラー API に切り替えてください](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)」を参照してください。

## 2019 年 9 月 20 日（PT）：バージョン 4.17.10

* 全般：Android API レベル 21 以降における、一部の地域のロケール文字列の生成を修正しました。

## 2019 年 7 月 18 日（PT）：バージョン 4.17.8

* Adobe Target：すべてのリクエストで、URL クエリパラメーターにクライアントおよび sessionId が含まれるようになりました。
* アプリ内メッセージ：空のクリックスルー URL でメッセージがトリガーされた場合に Android アプリがクラッシュする問題を修正しました。
* 訪問者 ID サービス：`Visitor.appendToURL` および `Visitor.getUrlVariablesAsync` API は、戻り値を二重エンコードしなくなりました。

   二重エンコードが原因で、API からの戻り値がセキュリティ診断によってリスクありと判断されることがありました。

## 2019 年 6 月 6 日（PT）：バージョン 4.17.7

* 全般 - Android API のレベル 20 未満でのネットワーク呼び出しで、TLS 1.1 または TLS 1.2 が使用されるようになりました。
* Analytics - プッシュ通知が有効な場合に、ライフサイクルデータにプッシュオプトインステータスを追加します。

## 2019 年 5 月 24 日（PT）：バージョン 4.17.6

* 訪問者 ID サービス： `setPushIdentifier` API 呼び出しは、呼び出されるたびに同期呼び出しを訪問者 ID サービスに送信するようになりました。
* 訪問者 ID サービス - 接続と読み取りのタイムアウトを 2 秒から 5 秒に増やしました。

すべてのソリューションに関する現在および過去のリリースノートについては、[Adobe Experience Cloud リリースノート](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=ja)を参照してください。
