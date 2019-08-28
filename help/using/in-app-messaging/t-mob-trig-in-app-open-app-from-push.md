---
description: アプリ内メッセージのトリガーは、ユーザーがプッシュメッセージからアプリを開いたときに送信されるプッシュメッセージ ID に設定できます。
seo-description: アプリ内メッセージのトリガーは、ユーザーがプッシュメッセージからアプリを開いたときに送信されるプッシュメッセージ ID に設定できます。
seo-title: プッシュメッセージからアプリを開いたときにアプリ内メッセージをトリガー
title: プッシュメッセージからアプリを開いたときにアプリ内メッセージをトリガー
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7

---


# Trigger an in-app message when the app is opened from a push message{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

アプリ内メッセージのトリガーは、ユーザーがプッシュメッセージからアプリを開いたときに送信されるプッシュメッセージ ID に設定できます。

1. ユーザーに送信されるプッシュメッセージのプッシュメッセージ ID を入手します。

   プッシュメッセージ ID は、メッセージ作成ワークフロー中に URL 内に見つけることができます。

   次に例を示します。

   ![](assets/brandon_task1.png)

1. 次のトリガーを設定したアプリ内メッセージを保存してから、アクティブ化します。

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >プッシュメッセージIDは、手順1にあるIDです。

   このトリガーは手動で追加する必要があります。**[!UICONTROL トリガー]ドロップダウンリストには含まれていません。**

   ![](assets/brandon_task2.png)

1. 手順 1 で見つけたプッシュ ID を持つプッシュメッセージを保存してから、送信します。
1. プッシュメッセージをクリックスルーしてアプリを開き、アプリが開いたときにアプリ内メッセージが表示されることを確認します。

   テストする際は、次の点に注意してください。

   * アプリ内メッセージを保存してから、ホストされている設定ファイルが新しいメッセージで更新されるまでに約 45 秒かかります。
   * **新規**&#x200B;起動がトリガーされると、アプリは設定ファイルのアップデート（新しいアプリ内メッセージ）を検索します。そのため、プッシュメッセージをクリックしたときにアプリで新規起動がトリガーされる必要があります。
   そのためには、通常、セッションがタイムアウトしていることを確認します。デフォルトのタイムアウトは 5 分です。
