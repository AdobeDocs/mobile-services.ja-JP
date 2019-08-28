---
description: Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。
seo-title: Experience Cloud ソリューション用 iOS SDK 4.x
solution: Marketing Cloud、Analytics
title: Experience Cloud ソリューション用 iOS SDK 4.x
topic: 開発者と導入
uuid: 8b374cee-1432-460b- aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud ソリューション用 iOS SDK 4.x{#ios-sdk-x-for-experience-cloud-solutions}

Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。

>[!IMPORTANT]
>
>Mobile Servicesの獲得、ディープリンク、位置情報およびモバイルメッセージング機能へのアクセスを有効にするには、Adobe Analytics Mobile Marketing Add- on SKUが必要です。詳しくは、Adobe CSMにお問い合わせください。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、Launch にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。

注意事項：

* iOS 5 以降がサポートされています。

   iOS 11 以降の場合は、SDK バージョン 4.13.8 以降を使用する&#x200B;**必要**&#x200B;があります。

* この SDK のバージョン 4.2 以降では、すべてのヒットが HTTP POST を使用して送信されるようになりました。

   これは収集またはレポートされるデータには影響しませんが、ヒットを表示するためにPOSTデータ検査をサポートするパケットアナライザーを使用する必要があります。

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile ユーザー向けドキュメント {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services は、モバイルアプリケーション用のモバイルマーケティング機能を Adobe Experience Cloud 上で統合する新しい UI を提供します。最初に、Mobileサービスは、Adobe Analytics、Adobe Audience ManagerおよびAdobe TargetソリューションおよびAdobe Experience Platform IDサービスのアプリ分析およびターゲット機能とのシームレスな統合を提供します。

Mobile Services UI の詳細を学習し、ユーザードキュメントを読むには、[Adobe Mobile Services](/help/using/home.md) を参照してください。

## Bloodhound の使用

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 2017 年 5 月 1 日以降、追加の機能強化や追加のエンジニアリングまたは Adobe Expert Care のサポートは提供されません。
