---
description: 日付範囲オプション、Analytics セグメントおよびカスタムセグメントを含む、プッシュメッセージのオーディエンスオプションを定義および設定できます。
keywords: モバイル
seo-description: 日付範囲オプション、Analytics セグメントおよびカスタムセグメントを含む、プッシュメッセージのオーディエンスオプションを定義および設定できます。
seo-title: オーディエンスプッシュメッセージ用のオーディエンスセグメントの定義と設定
solution: Marketing Cloud,Analytics
title: オーディエンスプッシュメッセージ用のオーディエンスセグメントの定義と設定
topic: 指標
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# オーディエンス：プッシュメッセージ{#audience-define-and-configure-audience-segments-for-push-messages}

日付範囲オプション、Analytics セグメントおよびカスタムセグメントを含む、プッシュメッセージのオーディエンスオプションを定義および設定できます。

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

レポートスイートまたは仮想レポートスイートには 1 つまたは複数のアプリからのデータが含まれるので、プッシュメッセージ用のオーディエンスセグメントが作成されると、そのセグメントには 1 つまたは複数のアプリからのユーザーが含まれます。仮想レポートスイートについて詳しくは、 [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

Adobe Mobile Services では、マーケターは、プラットフォームごとに 1 つのアプリにのみプッシュします。マーケターが複数のアプリからのユーザーを含むセグメントにプッシュしようとすると、処理が深刻なプッシュの失敗を引き起こし、ユーザーがブラックリストに記載される可能性があることを示す警告が表示されます。プッシュの失敗が発生した場合は、「プッシュメッセージの失敗の解決」**（ [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

セグメント定義で Audience Manager データを使用するには、[Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html) を参照してください。

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

複数のアプリにまたがるユーザーを含むオーディエンスセグメントを選択すると、次のアラートが表示される場合があります。

![複数のアプリ名](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>バージョン番号はオプションです。

最大 6 セットのバージョン番号と 5 セットのバンドル ID 番号が削除されます。

以下に例を示します。

* `Bea[rd]cons 1.0 (123)` は `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` は `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` は `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` は `Bea[rd]cons (.6)`

リストされたアプリにプッシュメッセージを送信し続けるには、「**はい、続行します。** チェックボックスをオンにして「送信」をク **[!UICONTROL リックしま]**&#x200B;す。

## ベストプラクティス

次に、覚えておくべきベストプラクティスをいくつか示します。

* 混乱を減らすために、複数のアプリからのデータを含むモバイルアプリ仮想レポートスイートを定義するのを&#x200B;**避けます**。
* プッシュメッセージを送信する際に、**毎回**、オーディエンスセグメントの一部として一意のアプリ ID を使用します。これにより、1 つのアプリ&#x200B;**のみ**&#x200B;に属するオーディエンスセグメントにプッシュ通知が送信されます。

### 例

次に、セグメントを正しく定義する方法を理解するのに役立ついくつかの例を示します。

**○**：マーケターが、1 つのアプリ（例：Adobe Photoshop）の iOS および Android バージョン用のプッシュ証明書を提供します。マーケターは、両方のプラットフォームにまたがるユーザーセグメントにプッシュ通知を送信することがあります。

**×**：マーケターが、1 つのアプリ（例：Adobe Photoshop）の iOS および Android バージョン用のプッシュ証明書を提供します。マーケターが&#x200B;*最近の 30 日間のすべてのアクティブユーザー*&#x200B;のセグメントを作成およびプッシュすると、Adobe Photoshop iOS および Android アプリのユーザーのみプッシュを受け取り、すべての Adobe Illustrator iOS および Android アプリのユーザーはブラックリストに記載されます。より詳細な例については、「プッシュメッセージの失敗の解決」**（ [プッシュメッセージのトラブルシューティング](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. 新しいプッシュメッセージを表示するには、オーディエンスページに移動します。

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * **[!UICONTROL 推定オプトインオーディエンス]**&#x200B;は、Adobe Analytics セグメントに合致するデバイスの数&#x200B;**および**&#x200B;オプトインしたデバイスの数です。

      選択したセグメントにおいて、メッセージの受信に同意（オプトイン）していて、プッシュメッセージを受信すると思われる推定ユーザー数を表示できます。推定数の下には、オプトイン状況を考慮しない、アプリユーザーの合計数が表示されます。

   * **[!UICONTROL 合計]は、Adobe Analytics セグメントに合致するデバイスの数です。**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      これは、SDK がプッシュメッセージオプトイン eVar に対して `True` の値を送信していることを意味します。

   * デバイスに有効なデバイストークンがある場合でも、Adobe Analyticsがオプトインフラグを設定していない限り、メッセージはデバイスにプッシュされません。

   * プッシュメッセージのトラブルシューティングについては、次を参照してください。

      * [iOSでのプッシュメッセージ](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Androidでのプッシュメッセージ](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. 次のフィールドに情報を入力します。

   * **[!UICONTROL 期間]**

      推定オーディエンスに使用する期間を入力します。**[!UICONTROL 期間]ドロップダウンリストから、次のいずれかのオプションを選択します。**

   * **[!UICONTROL 最近]**&#x200B;メッセージのプッシュがスケジュールされている日時からの相対期間（最近の 7 日間、最近の 30 日間、最近の 60 日間など）を選択できます。

      例えば、「最近の 30 日間」を選択して、メッセージを 10 月 31 日にプッシュするようにスケジュールした場合、推定オーディエンスは、10 月 31 日の 30 日前にプッシュメッセージの受信に同意していたユーザー数になります。

   * **[!UICONTROL 静的範囲]**&#x200B;推定オーディエンス範囲の開始日付と終了日付を選択することで、静的範囲を選択できます。

      前述の例を使用すると、10 月 1 日に始まり 10 月 15 日に終わる日付範囲を選択しつつ、メッセージをプッシュする日付を 10 月 31 日に設定した場合、推定オーディエンスは、指定した静的日付範囲（10 月 1 日～ 10 月 15 日）にプッシュメッセージの受信に同意していたユーザー数になります。

   * **[!UICONTROL Analytics セグメント]**

      ドロップダウンリストから既存のAdobe Analyticsセグメントを選択します。 For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL カスタムセグメント]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. 例えば、次のカスタムセグメントは、iOS が動作している携帯電話を所持し、カリフォルニア（米国）地域にいるユーザーをターゲットとしています。
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
