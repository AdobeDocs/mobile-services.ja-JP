---
description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
keywords: モバイル
seo-description: この情報は、プッシュメッセージのトラブルシューティングに役立ちます。
seo-title: プッシュメッセージのトラブルシューティング
solution: Experience Cloud,Analytics
title: プッシュメッセージのトラブルシューティング
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 100%

---

# プッシュメッセージのトラブルシューティング {#troubleshooting-push-messaging}

この情報は、プッシュメッセージのトラブルシューティングに役立ちます。

## プッシュメッセージの送信に遅延が生じることがある理由

Mobile Services のプッシュメッセージは、次のタイプの遅延を伴うことがあります。

* **Analytics のヒットの待機**

   どのレポートスイートにも、受信する Analytics のヒットをいつ処理するかを決定する設定があります。デフォルトは、1 時間ごとです。

   Analytics のヒットの実際の処理にかかる時間は最大 30 分ですが、通常は 15 ～ 20 分です。例えば、あるレポートスイートでは 1 時間ごとにヒットが処理されます。最大 30 分の処理時間を必要とする場合、受信ヒットをプッシュメッセージに使用できるようになるまでに最大 90 分かかる場合があります。あるユーザーがアプリを午前 9 時 1 分に起動した場合、ヒットが新しいユニークユーザーとして Mobile Services UI に表示されるのは、午前 10 時 15 分～ 10 時 30 分になります。

* **プッシュサービスの待機**

   プッシュサービス（APNS または GCM）は、メッセージを直ちに送信できないことがあります。めったに起こりませんが、5 ～ 10 分の待ち時間が生じます。プッシュメッセージの&#x200B;**[!UICONTROL レポート]**&#x200B;ビューを見て、**[!UICONTROL メッセージ履歴]**&#x200B;テーブルにあるメッセージを探し、**[!UICONTROL 発行数]**&#x200B;を確認することで、プッシュメッセージがプッシュサービスに送信されたことを確認できます。

   >[!TIP]
   >
   >この数は、成功したプッシュサービスへの送信件数です。プッシュサービスでは、メッセージが送信されることは保証されません。

   サービスの信頼性について詳しくは、次を参照してください。

   * [サービス品質](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [メッセージの有効期間](https://developers.google.com/cloud-messaging/concept-options#lifetime)

## Android GCM API キーが無効なのはなぜですか。

* **無効な API キー**

   次の理由で、API キーが無効となっている可能性があります。

   * 指定した API キーは、正しい GCM API キー値を持つサーバーキーではありません。
   * サーバーキーは IP を許可し、アドビのサーバーがプッシュメッセージを送信するのをブロックしています。

* **API キーの有効性の判断**

   API キーの有効性を判断するには、次のコマンドを実行します。

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   返された 401 HTTP ステータスコードは、APIキーが無効であることを意味します。それ以外の場合は、次のようになります。

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   また、「`"ABC"`」をトークンと置き換えることで、登録トークンの有効性をチェックできます。

## APNS 証明書が機能しない理由

次の理由で、APNS 証明書が無効になっている可能性があります。

* 実稼働版証明書の代わりにサンドボックス証明書を使用している可能性があります。
* サポートされていない新しい実稼動／サンドボックス証明書を使用しています。
* `.p8` ファイルではなく、`.p12` ファイルを使用しています。

## プッシュメッセージの失敗の解決

**例**

次の例は、VRS を使用した場合のプッシュ失敗の解決方法を示しています。

次のお客様には iOS アプリが 2 つあります。

* アプリ名：PhotoShop_app_iOS
   * 親 RSID：AllAdobe PhotoShop_apps
   * VRSID：PhotoShop_iOS_app_SF
   * VRSID 定義セグメント：`a.appid contains “PhotoShop_iOS_app_SF”`
* アプリ名：PhotoShop_app_iOS
   * 親 RSID：AllAdobe PhotoShop_apps
   * RSID：PhotoShop_iOS_app_LA
   * VRSID 定義セグメント：`a.os contains “iOS”`

この例では、Photoshop ユーザーが *PhotoShop_iOS_app_SF* アプリにプッシュを送信すると、すべての *PhotoShop_iOS_app_SF*&#x200B;アプリユーザーが期待どおりにプッシュメッセージを受け取ります。しかし、ユーザーが *PhotoShop_iOS_app_LA*&#x200B;アプリにメッセージを送信すると、その VRSID 定義セグメントが正しくない（`a.os contains "PhotoShop_iOS_app_LA"` ではなく `iOS` となっている）ので、*AllAdobe PhotoShop_apps* の&#x200B;**すべての** iOS ユーザーにメッセージが送信されます。メッセージは依然として *PhotoShop_iOS_app_LA* ユーザーに届きますが、*PhotoShop_iOS_app_SF* アプリの証明書が異なるので、メッセージは&#x200B;*PhotoShop_iOS_app_SF* ユーザーのプッシュ ID をブロックリストに記載します。セグメントが `a.os contains “PhotoShop_iOS_app_LA”` と定義されていた場合、プッシュメッセージは&#x200B;*PhotoShop_iOS_app_LA*&#x200B;ユーザーにのみ送信されていました。

*PhotoShop_IOS_app_LA* プッシュ証明書を使用して渡された場合、*PhotoShop_iOS_app_SF* のプッシュ ID は `invalid` として復活します。

>[!CAUTION]
>
>VRS を使用しているアプリ用にプッシュメッセージを作成して **[!UICONTROL 保存して送信]** をクリックすると、リストされている各アプリに有効な証明書がある&#x200B;**必要がある**&#x200B;ことを確認するアラートが表示されます。各アプリに有効な証明書が&#x200B;**ない**&#x200B;場合、オーディエンスセグメントは無期限にブロックリストに記載され、今後、影響を受けるユーザーにプッシュメッセージを送信できなくなる可能性があります。オーディエンスセグメントについて詳しくは、「[オーディエンス：プッシュメッセージ用のオーディエンスオプションの定義および設定](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)」を参照してください。
