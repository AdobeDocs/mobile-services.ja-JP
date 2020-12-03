---
description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
seo-title: プライバシーと一般データ保護規則
title: プライバシーと一般データ保護規則
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 74%

---


# プライバシーと一般データ保護規則 {#privacy-and-general-data-protection-regulation}

データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。

>[!IMPORTANT]
>
>GDPR は Mobile SDK バージョン 4.16.0 以降で&#x200B;**のみ**&#x200B;サポートされています。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## 概要

Adobeが企業にソフトウェアやサービスを提供する場合、Adobeは、個人データの処理や保存の一環として、個人データのデータ処理装置としての役割を果たします。 データ処理装置として、Adobeは、会社の許可と指示に従って個人データを処理します(例えば、Adobeとの契約に基づいて設定されたもの)。

データコントローラーは、AdobeMobile Services SDKを使用して、GDPRによるモバイルアプリの取得および削除のリクエストをサポートできます。

モバイルアプリケーションの Adobe Mobile SDK 部分に関しては、次の設定とメソッドを使用できます。

* SDK からデータを取得してサーバーに送信するには、`getAllIdentifiersAsync` メソッドを使用します。

   詳しくは、「[保存されている ID の取得](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)」を参照してください。

* オプトステータスを設定して GDPR データ削除要求を処理するには、次の設定を使用します。

   * `privacyDefault`
   * `setPrivacyStatus`

   詳しくは、「[ユーザーのオプトステータスの設定](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)」を参照してください。

## 追加情報 {#section_7C7124C50D85469C8C8714533FB1A37D}

* GDPRの詳細については、「 [GDPRとYour Business](https://www.adobe.com/jp/privacy/general-data-protection-regulation.html)」を参照してください。
* To see the GDPR API documentation, go to [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html).

