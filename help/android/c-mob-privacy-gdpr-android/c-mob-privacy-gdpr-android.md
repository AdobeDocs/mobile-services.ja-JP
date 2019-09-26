---
description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-title: プライバシーと一般的なデータ保護規制の概要
title: プライバシーと一般的なデータ保護規制の概要
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。

## New Adobe Experience Platform Mobile SDK Release

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* To get started, go to Adobe Experience Platform Launch.
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## 概要

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

アドビが企業に対してソフトウェアやサービスを提供する場合、アドビはサービス提供の一環として同社が処理または保管する個人データのデータ処理事業者に該当します。データ処理事業者に位置付けられるアドビはお客様の許可と指示（アドビとお客様の間で定められた合意など）に基づき個人データを処理します。

データ管理事業者に位置付けられるお客様は Adobe Mobile Services SDK を使用することでお客様のモバイルアプリケーションから送信された GDPR 取得要求や GDPR 削除要求に対処できます。

モバイルアプリケーションの Adobe Mobile SDK 部分に関しては、次の設定とメソッドを使用できます。

* SDK からデータを取得してサーバーに送信するには、`getAllIdentifiersAsync` メソッドを使用します。

   For more information, see Retrieving Stored Identifiers.[](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)

* オプトステータスを設定して GDPR データ削除要求を処理するには、次の設定を使用します。

   * `privacyDefault`
   * `setPrivacyStatus`
   For more information, see Setting the User's Opt Status.[](/help/android/c-mob-privacy-gdpr-android/privacy.md)