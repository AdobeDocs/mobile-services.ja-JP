---
description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
keywords: モバイル
seo-description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
seo-title: プッシュメッセージのトラブルシューティング
solution: Marketing Cloud,Analytics
title: プッシュメッセージのトラブルシューティング
topic: 指標
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

この情報は、プッシュメッセージのトラブルシューティングに役立ちます。

## プッシュメッセージの送信に遅延が生じることがある理由

Mobile Services のプッシュメッセージは、次のタイプの遅延を伴うことがあります。

* **Analyticsのヒットを待機中**

   どのレポートスイートにも、受信する Analytics のヒットをいつ処理するかを決定する設定があります。デフォルトは、1 時間ごとです。

   Analytics のヒットの実際の処理にかかる時間は最大 30 分ですが、通常は 15 ～ 20 分です。例えば、1 時間ごとにヒットを処理するレポートスイートがあるとします。最大 30 分の必要な処理時間を考慮に入れると、プッシュメッセージに対して受信ヒットが利用可能になるまでに最大 90 分かかる場合があります。あるユーザーがアプリを午前 9 時 1 分に起動した場合、ヒットが新しい一意のユーザーとして Mobile Services UI に表示されるのは、午前 10 時 15 分～ 10 時 30 分になります。

* **プッシュサービスの待機**

   プッシュサービス（APNS または GCM）は、メッセージを直ちに送信できないことがあります。めったに起こりませんが、5 ～ 10 分の待ち時間が生じます。プッシュメッセージの&#x200B;**[!UICONTROL レポート]**&#x200B;ビューを見て、**[!UICONTROL メッセージ履歴]テーブルにあるメッセージを探し、**&#x200B;発行数]を確認することで、プッシュメッセージがプッシュサービスに送信されたことを確認できます。**[!UICONTROL **

   >[!TIP]
   >
   >This count is the number of successful sends to the Push Service(s). プッシュサービスでは、メッセージが送信されることは保証されません。

   サービスの信頼性について詳しくは、次を参照してください。

   * [サービス品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [メッセージの有効期間](https://developers.google.com/cloud-messaging/concept-options#lifetime)。

## Android GCM API キーが無効である理由

* **無効な API キー**

   次の理由により、API キーが無効になっていることがあります。

   * 指定した API キーが正しい GCM API キー値を持つサーバーキーでない。
   * サーバーキーは、ホワイトリストに登録された IP で、アドビのサーバーがプッシュメッセージを送信するのをブロックします。

* **API キーの有効性の判定**

   API キーの有効性を判定するには、次のコマンドを実行します。

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   返される 401 HTTP ステータスコードは、API キーが無効であることを意味します。そうでない場合は、次のようなものが表示されます。

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## APNS 証明書が機能しない理由

次の理由により、APNS 証明書が無効になっていることがあります。

* 実稼動証明書ではなく、サンドボックス証明書を使用している可能性があります。
* サポートされていない新しい実稼動／サンドボックス証明書を使用している可能性があります。
* You are using `.p8` file instead of a `.p12` file.

## プッシュメッセージの失敗の解決

**An example**

次の例は、VRS 使用時のプッシュエラーを解決する方法を示しています。

次の顧客は、2 つの iOS アプリを持っています。

* アプリ名：PhotoShop_app_iOS
   * Parent RSID：AllAdobe PhotoShop_apps
   * VRSID：PhotoShop_iOS_app_SF
   * VRSID Definition Segment: `a.appid contains “PhotoShop_iOS_app_SF”`
* アプリ名：PhotoShop_app_iOS
   * Parent RSID：AllAdobe PhotoShop_apps
   * RSID:PhotoShop_iOS_app_LA
   * VRSID Definition Segment: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. 各アプリに有効な証明書が&#x200B;**ない**&#x200B;場合、オーディエンスセグメントは無期限にブラックリストに記載され、今後、影響を受けるユーザーにプッシュメッセージを送信できなくなる可能性があります。オーディエンスセグメントについて詳しくは、オーディエンスを参照し [てください。プッシュメッセージのオーディエンスオプションを定義し、設定します](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。
