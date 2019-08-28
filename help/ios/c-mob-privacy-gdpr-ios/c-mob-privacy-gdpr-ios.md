---
description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-title: プライバシーと一般データ保護規則
title: プライバシーと一般データ保護規則
uuid: 69bb82de-1993-440c- a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# プライバシーと一般データ保護規則 {#privacy-and-general-data-protection-regulation}

データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

アドビが企業に対してソフトウェアやサービスを提供する場合、アドビはサービス提供の一環として同社が処理または保管する個人データのデータ処理事業者に該当します。データ処理事業者に位置付けられるアドビはお客様の許可と指示（アドビとお客様の間で定められた合意など）に基づき個人データを処理します。

データ管理事業者に位置付けられるお客様は Adobe Mobile Services SDK を使用することでお客様のモバイルアプリケーションから送信された GDPR 取得要求や GDPR 削除要求に対処できます。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、Launch にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。


モバイルアプリケーションの Adobe Mobile SDK 部分に関しては、次の設定とメソッドを使用できます。

* SDK からデータを取得してサーバーに送信するには、`getAllIdentifiersAsync` メソッドを使用します。

   詳しくは、「格納済み識別子 [の取得](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)」を参照してください。

* オプトステータスを設定して GDPR データ削除要求を処理するには、次の設定を使用します。

   * `privacyDefault`
   * `setPrivacyStatus`
   詳しくは、「ユーザーのオプトステータス [の設定](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)」を参照してください。

## 追加情報 {#section_7C7124C50D85469C8C8714533FB1A37D}

* GDPR について詳しくは、[GDPR とビジネス](https://www.adobe.com/privacy/general-data-protection-regulation.html)を参照してください。
* GDPR API ドキュメントについて詳しくは、[一般データ保護規則 API](https://adobe.io/apis/cloudplatform/gdpr.html) を参照してください。

