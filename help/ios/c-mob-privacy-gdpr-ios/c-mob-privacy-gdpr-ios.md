---
description: データ管理事業者は Experience Cloud Mobile SDK で提供されている一般データ保護規則（GDPR）対応 API を利用することで、ユーザーがローカルに保存されている個人情報を取得したり、データ収集やデータ送信のオプトステータスフラグを設定したりできる環境を開発することができます。
title: プライバシーと一般データ保護規則
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 71%

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

Adobeが企業に対してソフトウェアやサービスを提供する場合、Adobeは、サービスの一部として処理および保存する個人データのデータ処理者としての役割を果たします。 Adobeはデータ処理者として、お客様の許可と指示 ( お客様とAdobeとの間で締結された契約の内容など ) に従って個人データを処理します。

データ管理者は、AdobeMobile Services SDK を使用して、モバイルアプリからの GDPR の取得および削除要求をサポートできます。

モバイルアプリケーションの Adobe Mobile SDK 部分に関しては、次の設定とメソッドを使用できます。

* SDK からデータを取得してサーバーに送信するには、`getAllIdentifiersAsync` メソッドを使用します。

   詳しくは、「[保存されている ID の取得](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)」を参照してください。

* オプトステータスを設定して GDPR データ削除要求を処理するには、次の設定を使用します。

   * `privacyDefault`
   * `setPrivacyStatus`

   詳しくは、「[ユーザーのオプトステータスの設定](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)」を参照してください。

## 追加情報 {#section_7C7124C50D85469C8C8714533FB1A37D}

* GDPR の詳細については、「[GDPR とお客様のビジネス ](https://www.adobe.com/jp/privacy/general-data-protection-regulation.html)」を参照してください。
* GDPR API のドキュメントを参照するには、[EU 一般データ保護規則 API](https://adobe.io/apis/cloudplatform/gdpr.html) に移動してください。
