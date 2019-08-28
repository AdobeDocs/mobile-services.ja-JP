---
description: この情報は、アプリ内メッセージのトラブルシューティングに役立ちます。
keywords: モバイル
seo-description: この情報は、アプリ内メッセージのトラブルシューティングに役立ちます。
seo-title: アプリ内メッセージのトラブルシューティング
solution: Marketing Cloud、Analytics
title: アプリ内メッセージのトラブルシューティング
topic: 指標
uuid: 39c3a21d-92c2-4004- b00f-99b6f91d3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# アプリ内メッセージのトラブルシューティング{#troubleshooting-in-app-messaging}

この情報は、アプリ内メッセージのトラブルシューティングに役立ちます。

アプリ内メッセージのすべての要件を満たしているにもかかわらずメッセージが表示されない場合は、以下の項目を確認してください。

## アプリで新しい設定および新しい SDK を使用する場合

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Android で全画面表示のメッセージが表示されません。正しい SDK と設定を使用しており、トリガーの条件は満たしています。

マニフェストファイルを更新して、全画面表示アクティビティを定義しているか確認してください。

## Android でローカルの通知メッセージが動作しません。

マニフェストにローカルの通知ブロードキャスト受信者が宣言されていることを確認します。For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## メッセージが発行されているか確認したい場合

メッセージが発行されているかどうかを確認するには、アプリ内メッセージを管理ページの&#x200B;**ステータス**&#x200B;列で、メッセージのリストを確認します。

## 一度 *表示*&#x200B;し、常に *表示して、「**オーディエンス」タブでオフライン* 設定を表示します。

これらの設定が正しく行われていることを確認します。「**[!UICONTROL 閲覧者]**」タブで、メッセージの表示頻度を指定するための「**トリガー[!UICONTROL 」オプションを確認します。]**

## 起動イベントをトリガーとして使用する場合

起動イベントは、新規セッションでのみ実行されます。セッションが開始されるタイミングについて詳しくは、`lifecycleTimeout`JSON 設定[の ](/help/android/configuration/json-config/json-config.md) の行を参照してください。

## メッセージをリモートで更新しましたが、アプリで古いメッセージが表示されます。

次の情報に留意してください。

* Dynamic Tag Management では、エンドポイントが新しい定義で更新されるまでに数分かかることがあります。しばらく待ってからもう一度試してください。
* 設定は、新たに起動したときにのみ更新されます。ライフサイクルセッションのタイムアウト時間中にアプリを再起動した場合は、新しい設定がダウンロードされていない可能性があります。

詳しくは、 [ライフサイクル指標](/help/android/metrics.md).

## 画像がテンプレートに用意されている領域にぴったりと収まりません。

アプリ内メッセージのフルスクリーンテンプレートは、リモートサーバー（画像 URL）またはアプリバンドル（バンドルされている画像）からの画像の表示をサポートしています。画像は、JPG、GIF、PNG などの、標準的な画像形式であることが必要です。デバイスの画面のサイズには様々なものがあるので、画像がテンプレートに用意されている領域にぴったりと収まらない可能性があります。テンプレートでは、画像の中心を表示することに重点が置かれており、画像が収まらない場合は端がトリミング（縦長）またはフェード（横長）されます。

それぞれの向きの正確な配置およびサイズ指定ルールを次に示します。

* **縦**
   * 高さ 195 px（携帯電話の場合）.
   * 高さ 529 px（タブレットの場合）.
   * 画像の幅がデバイスの幅より小さい場合は中央に表示されます。
   * 画像の幅がデバイスの幅より大きい場合はトリミングされます。

* **横**
   * 画像は、デバイスの高さの 100％に拡大または縮小されます。
   * 幅はデバイスの 75％で、右側がフェードアウトします。
   フルスクリーンテンプレートに問題がある場合は、カスタム HTML テンプレートをダウンロードして使用できます。このテンプレートでは、より柔軟に画像を表示でき、テンプレートを自由にカスタマイズできます。
