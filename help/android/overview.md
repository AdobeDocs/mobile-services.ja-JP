---
description: Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。
keywords: android;library;mobile;sdk
seo-description: Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。
seo-title: Experience Cloud ソリューション用 Android SDK 4.x
solution: Marketing Cloud、Analytics
title: Experience Cloud ソリューション用 Android SDK 4.x
topic: 開発者と導入
uuid: 56f1ff41-0365-41dd- bdtr-245c823dff07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。

>[!IMPORTANT]
>
>Mobile Servicesの獲得、ディープリンク、位置情報およびモバイルメッセージング機能へのアクセスを有効にするには、Adobe Analytics Mobile Marketing Add- on SKUが必要です。詳しくは、Adobe CSMにお問い合わせください。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

>[!IMPORTANT]
>
>2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、[Launch](https://launch.adobe.com/) にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。

>[!IMPORTANT]
>
>UIで機能を設定することはできますが、生成された設定ファイルをダウンロードしてSDKに追加するまで、これらの機能は機能しません。SDKのダウンロードと設定について詳しくは [、コアの実装とライフサイクル](/help/android/getting-started/dev-qs.md)を参照してください。

SDK は、Android の次のバージョンをサポートしています。

* バージョン 4.6.0 以前では、Android 2.2（API 8）から Android 5.1.1（API 22）までがサポートされます。
* バージョン4.6.1 以降では、Android 2.3（API 9）以降がサポートされます。

注意事項：

* バージョン 4.2 以降では、すべてのヒットが HTTP POST を使用して送信されるようになりました。

   これは収集またはレポートされるデータには影響しませんが、ヒットを表示するためにPOSTデータ検査をサポートするパケットアナライザーを使用する必要があります。

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services は、Adobe Experience Cloud の各種モバイルアプリケーションのモバイルマーケティング機能を統合する UI を提供します。UI の詳細とユーザー向けドキュメントについては、[Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/) を参照してください。

## リリースノート {#section_F8181DC052D44DD2A99AB40A41F6792C}

Experience Cloud リリースの最新情報については、[Experience Cloud リリースノート](https://marketing.adobe.com/resources/help/en_US/whatsnew/)を参照してください。

## Bloodhound の使用

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. 2017 年 5 月 1 日以降、追加の機能強化や追加のエンジニアリングまたは Adobe Expert Care のサポートは提供されません。
