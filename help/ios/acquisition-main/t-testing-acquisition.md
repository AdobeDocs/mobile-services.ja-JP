---
description: デバイス指紋に基づく従来の獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-description: デバイス指紋に基づく従来の獲得キャンペーンリンクのラウンドトリップに役立つ情報です。
seo-title: 従来の獲得のテスト
solution: Marketing Cloud、Analytics
title: 従来のダウンロード計測のテスト
uuid: e0591f4a- e26b-4fe4-97c1- a6831a926fa5
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testing legacy acquisition {#testing-legacy-acquisition}

デバイス指紋に基づく従来の獲得キャンペーンリンクのラウンドトリップに役立つ情報です。

モバイルアプリがまだ Google Play にない場合は、キャンペーンリンクの作成時に任意のモバイルアプリをリンク先として選択できます。これは、ダウンロード計測用リンクのクリック後に獲得サーバーによってリダイレクトされるアプリにのみ影響を与えます。ダウンロード計測用リンクのテスト機能には影響を与えません。

1. Navigate to **[!UICONTROL Use Legacy Acquisition Links]** in Adobe Mobile Services and generate an acquisition campaign URL.

   詳しくは、[従来のダウンロード計測用リンクの使用](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)を参照してください。

1. アプリをインストールするモバイルデバイスから、生成したリンクをクリックします。

   アドビのサーバー（`c00.adobe.com`）がデバイス指紋を保存し、App Store にリダイレクトします。テストのためにアプリをダウンロードする必要はありません。

1. 手順 2 で使用したのと同じモバイルデバイスで、アプリケーションを初めて起動します。

   最も簡単な方法は、アプリを削除してから再度インストールすることです。

次の情報に留意してください。

* 獲得サーバーは、リンクのクリック（手順 2）とアプリの起動時（手順 3）に記録された IP アドレスとユーザーエージェント情報に基づいて、アトリビューションを一致させます。
* HTTP モニタリングツールを使用することによって、アプリから送信されるヒットを監視して、獲得アトリビューションを確認できます。

>[!TIP]
>
>送信されたユーザーエージェントが変わると、アトリビューションが失敗することがあります。
