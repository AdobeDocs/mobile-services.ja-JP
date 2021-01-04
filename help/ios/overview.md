---
description: Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。
seo-description: Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。
seo-title: Experience Cloud ソリューション用 iOS SDK 4.x
solution: Experience Cloud,Analytics
title: Experience Cloud ソリューション用 iOS SDK 4.x
topic: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: c7400359bc19150926a67b991ba219a7fa187442
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 100%

---


# Experience Cloud ソリューション用 iOS SDK 4.x {#ios-sdk-x-for-experience-cloud-solutions}

Experience Cloud ソリューション用 iOS SDK 4.x を使用すると、ネイティブの Apple iPhone および iPad アプリケーションを測定したり、アプリ内からターゲットコンテンツを配信したり、Audience Manager でオーディエンスデータを活用および収集したりできます。

>[!IMPORTANT]
>
>バージョン 4.21.0 以降、iOS SDK には必要最小限の Xcode 12 のバージョンがあります。 Cocoapods を使用してアプリ内の依存関係を管理する場合、Adobe SDK には Cocoapods バージョン 1.10.0 以降が必要です。

4.21.0 以降を使用している場合は、次の変更を考慮してドキュメントを一読してください。

* バイナリライブラリファイルについて言及されている場合は常に、 XCFramework に置き換えて使用する必要があります。
   * `AdobeMobileLibrary.a`／`AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a`／`AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a`／`AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a`／`AdobeMobileTV.xcframework`
* Adobe XCFrameworks を手動でプロジェクトに追加する場合は、埋め込まれていないことを確認してください。

>[!IMPORTANT]
>
>Mobile Services でモバイル獲得、ディープリンク、位置情報およびモバイルメッセージング機能を利用するには、Adobe Analytics Mobile Marketing アドオン SKU が必要です。詳しくは、Adobe CSM にお問い合わせください。

>[!IMPORTANT]
>
>Experience Cloud ソリューション用 iOS SDK 4.x で、[iOS 13 および Xcode 11](https://developer.apple.com/ios/) をサポートするようになりました。シームレスな互換性を確保するには、4.x iOS SDK の最新バージョンを使用してください。最新バージョンについて詳しくは、[リリースノート](/help/ios/rel-notes.md)を参照してください。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

注意事項：

* iOS 8 以降がサポートされています。

   iOS 11 以降の場合は、SDK バージョン 4.13.8 以降が&#x200B;**必要です**。

* この SDK のバージョン 4.2 以降では、すべてのヒットが HTTP POST を使用して送信されるようになりました。

   収集またはレポートされるデータに影響はありませんが、ヒットを調べるにるには、POST データの検査をサポートするパケットアナライザーを使用する必要があります。

* 以前のバージョン（2.x または 3.x）からアップグレードする場合は、「[4.x 移行ガイド](/help/ios/getting-started/migration-v3.md)」を参照してください。

## Adobe Mobile ユーザードキュメント {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services は、モバイルアプリケーション用のモバイルマーケティング機能を Adobe Experience Cloud 上で統合する新しい UI を提供します。最初に、Mobile Services が Adobe Analytics、Adobe Audience Manager および Adobe Target のソリューションと、Adobe Experience Platform ID サービスのアプリ分析およびターゲティング機能をシームレスに統合します。

Mobile Services UI の詳細を学習し、ユーザードキュメントを読むには、[Adobe Mobile Services](/help/using/home.md) を参照してください。

## Bloodhound の使用

>[!IMPORTANT]
>
>Adobe Bloodhound は、**2017 年 4 月 30 日**&#x200B;をもって廃止されました。2017 年 5 月 1 日以降、追加の機能強化や追加のエンジニアリングまたは Adobe Expert Care のサポートは提供されません。
