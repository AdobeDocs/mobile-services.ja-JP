---
description: 獲得追跡は、マーケティングリンクを追跡してレポートする前に、SDK設定で有効にする必要があります。
keywords: モバイル
seo-description: 獲得追跡は、マーケティングリンクを追跡してレポートする前に、SDK設定で有効にする必要があります。
seo-title: 獲得の設定
solution: Marketing Cloud、Analytics
title: 獲得の設定
topic: 指標
uuid: e996e43e-8a77-47a3- a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# 獲得の設定 {#configure-acquisition}

獲得追跡は、マーケティングリンクを追跡してレポートする前に、SDK設定で有効にする必要があります。

1. アプリのアプリ設定ページで、「**[!UICONTROL SDK からの獲得データ送信]**」セクションまでスクロールします。
1. 次のタスクを実行します。

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * **[!UICONTROL 「リファラータイムアウト（秒）]** 」フィールドに値を入力します

      **（オプション**） **[!UICONTROL 「有効」]** チェックボックスを有効にした場合、このフィールドはオプションです。タイムアウト値を変更できます。秒単位で指定します。この設定では、最初の起動ヒットを送信する前に、獲得情報を待機する期間を指定します。
   >[!IMPORTANT]
   >ゼロ以外の値を入力する必要があります。獲得を有効にし、値をゼロとして残すと、ダウンロード計測用リンクは機能しません。デフォルト値の5秒を使用することをお勧めします。

1. アプリの新しい SDK 設定ファイルをダウンロードして使用します。

   **iOS** で獲得が正常に設定されました。**Android**&#x200B;で獲得を有効にするには、モバイル獲得 [の追跡の手順を実行](/help/android/acquisition-main/acquisition.md)します。
