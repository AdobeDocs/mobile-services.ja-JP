---
description: 新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページで SDK からの獲得データ送信を設定できます。
keywords: モバイル
solution: Experience Cloud Services,Analytics
title: SDK からの獲得データ送信の設定
topic-fix: Metrics
uuid: 50ce51ad-39bf-4ac7-bd94-757443d11ca7
exl-id: 72ab6777-88b5-4908-9d0f-7f68f298dad1
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 100%

---

# SDK からの獲得データ送信の設定 {#configure-sdk-acquisition-options}

{#eol}

新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページで SDK からの獲得データ送信を設定できます。

1. **[!UICONTROL SDK からの獲得データ送信オプション]** の下で、次のフィールドに情報を入力します。

   * **[!UICONTROL 有効にする]**

      ユーザーが Apple App Store や Google Play からアプリを直接ダウンロードできるアプリストアリンクを作成します。これにより、単なるダウンロード回数に加えて、このリンク経由でアプリをダウンロードした後のユーザー行動（ライフサイクル系指標や成功イベント）を長期で追えるようになります。詳しくは、「[獲得](/help/using/acquisition-main/acquisition-main.md)」を参照してください。

   * **[!UICONTROL 送信タイムアウト（秒）]**

      送信タイムアウト値を指定します。

      デフォルト値は 5 秒です。この値には、アプリストアへのリンクに含まれるダウンロード計測用データをサーバーに送信する際のタイムアウト設定を秒単位で指定します。

   * **[!UICONTROL さらに詳細を表示]**

      **[!UICONTROL さらに詳細を表示]** リンクをクリックすると、アプリのトラッキング ID が表示されます。
