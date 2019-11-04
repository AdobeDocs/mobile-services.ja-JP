---
description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-title: プライバシーと EU 一般データ保護規則の概要
title: プライバシーと EU 一般データ保護規則の概要
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# プライバシーと EU 一般データ保護規則の概要 {#privacy-and-general-data-protection-regulation}

データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## 概要

>[!IMPORTANT]
>
>GDPR は Mobile SDK バージョン 4.16.0 以降で&#x200B;**のみ**&#x200B;サポートされています。

アドビが企業に対してソフトウェアやサービスを提供する場合、アドビはサービス提供の一環として同社が処理または保管する個人データのデータ処理事業者に該当します。データ処理事業者に位置付けられるアドビはお客様の許可と指示（アドビとお客様の間で定められた合意など）に基づき個人データを処理します。

データ管理事業者に位置付けられるお客様は Adobe Mobile Services SDK を使用することでお客様のモバイルアプリケーションから送信された GDPR 取得要求や GDPR 削除要求に対処できます。

モバイルアプリケーションの Adobe Mobile SDK 部分に関しては、次の設定とメソッドを使用できます。

* SDK からデータを取得してサーバーに送信するには、`getAllIdentifiersAsync` メソッドを使用します。

   詳しくは、「[保存されている ID の取得](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)」を参照してください。

* オプトステータスを設定して GDPR データ削除要求を処理するには、次の設定を使用します。

   * `privacyDefault`
   * `setPrivacyStatus`
   詳しくは、「[ユーザーのオプトステータスの設定](/help/android/c-mob-privacy-gdpr-android/privacy.md)」を参照してください。