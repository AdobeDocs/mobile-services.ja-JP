---
description: Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。
keywords: android;library;mobile;sdk
seo-description: Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。
seo-title: Experience Cloud ソリューション用 Android SDK 4.x
solution: Experience Cloud,Analytics
title: Experience Cloud ソリューション用 Android SDK 4.x
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---


# Experience Cloud ソリューション用 Android SDK 4.x {#android-sdk-x-for-experience-cloud-solutions}

Experience Cloud ソリューション用 Android SDK 4.x を使用すると、ネイティブ Android アプリケーションを測定したり、ターゲットコンテンツをアプリに配信したり、Audience Management を通じて視聴者データを活用および収集したりすることができます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
>Mobile Services でモバイル獲得、ディープリンク、位置情報およびモバイルメッセージング機能を利用するには、Adobe Analytics Mobile Marketing アドオン SKU が必要です。詳しくは、Adobe CSM にお問い合わせください。

>[!IMPORTANT]
>
>UI で機能を設定できますが、これらの機能は、生成された設定ファイルをダウンロードして、このファイルを SDK に追加するまでは機能しません。SDK のダウンロードと設定について詳しくは、「[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)」を参照してください。

SDK は、次のバージョンの Android をサポートしています。

* バージョン 4.6.0 以前では、Android 2.2（API 8）から Android 5.1.1（API 22）までがサポートされます。
* バージョン 4.6.1 以降では、Android 2.3（API 9）以降がサポートされます。

注意事項：

* バージョン 4.2 以降では、すべてのヒットが HTTP POST を使用して送信されるようになりました。

   収集またはレポートされるデータに影響はありませんが、ヒットを調べるにるには、POST データの検査をサポートするパケットアナライザーを使用する必要があります。

* 以前のバージョンからアップグレードする場合は、「[4.x 移行ガイド](/help/android/getting-started/migration-v3.md)」を参照してください。

## Adobe Mobile ユーザードキュメント {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services は、Adobe Experience Cloud の各種モバイルアプリケーションのモバイルマーケティング機能を統合する UI を提供します。UI の詳細を学習し、ユーザードキュメントを読むには、[Adobe Mobile Services](https://docs.adobe.com/content/help/ja-JP/mobile-services/using/home.html) を参照してください。

## リリースノート {#section_F8181DC052D44DD2A99AB40A41F6792C}

Experience Cloud リリースの最新情報については、[Experience Cloud リリースノート](https://docs.adobe.com/content/help/ja-JP/release-notes/experience-cloud/current.html)を参照してください。

## Bloodhound の使用

>[!IMPORTANT]
>
>Adobe Bloodhound は、**2017 年 4 月 30 日**&#x200B;をもって廃止されました。2017 年 5 月 1 日以降、追加の機能強化や追加のエンジニアリングまたは Adobe Expert Care のサポートは提供されません。
