---
description: Adobe Mobile Services のテクニカルドキュメント
seo-description: このガイドでは、Adobe Mobile Services のテクニカルドキュメントとセルフヘルプについて説明します。Adobe Mobile Services には、モバイルアプリケーションのユーザーエンゲージメントを把握して改善できるよう、Adobe Experience Cloud 全体のモバイルアプリケーション用のモバイルマーケティング機能がまとめられています。
seo-title: Adobe Mobile Services
solution: Experience Cloud, Analytics, Experience Cloud
title: Adobe Mobile Services
uuid: e86a77c9-4ff1-403f-a5a1-4afbdc4e6f68
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 100%

---


# Adobe Mobile Services {#adobe-mobile-services}

このガイドでは、Adobe Mobile Services のテクニカルドキュメントとセルフヘルプについて説明します。Adobe Mobile Services には、モバイルアプリケーションのユーザーエンゲージメントを把握して改善できるよう、Adobe Experience Cloud 全体のモバイルアプリケーション用のモバイルマーケティング機能がまとめられています。

>[!IMPORTANT]
>
>Mobile Services でモバイル獲得、ディープリンク、位置情報およびモバイルメッセージング機能を利用するには、Adobe Analytics Mobile Marketing アドオン SKU が必要です。詳しくは、Adobe CSM にお問い合わせください。

## 4x SDK のサポート終了のお知らせ

2020 年 10 月 1 日以降、お客様は引き続きバージョン 4 の SDK をダウンロードして使用できますが、カスタマーケアのサポートやフォーラムへのアクセスは利用できません。Adobe Experience Platform Mobile SDK（旧称 v5）は、今後の Adobe Experience Cloud の機能のみをサポートする予定です。

詳しくは、サポート終了の [FAQ](https://aep-sdks.gitbook.io/docs/version-4-sdk-end-of-support-faq) を参照してください。

可能な場合は、新しい Experience Platform Mobile SDK に移行することをお勧めします。

## 新しい Adobe Experience Cloud SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 利用を開始するには、Launch にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> Adobe Experience Platform Mobile SDK を Adobe Launch で使用している場合、アプリ内メッセージ、プッシュ通知、またはダウンロード計測用リンクなどの機能を使用するには、Adobe Analytics Mobile Services 拡張機能もインストールする&#x200B;**必要があります**。詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。

>[!IMPORTANT]
>
>UI で機能を設定できますが、これらの機能は、生成された設定ファイルをダウンロードして、このファイルを SDK に追加するまでは機能しません。SDK のダウンロードと設定について詳しくは、本ページの *SDK ドキュメント*&#x200B;の節を参照してください。

最新のリリースノートについては、「[Experience Cloud リリースノート](https://docs.adobe.com/content/help/ja-JP/release-notes/experience-cloud/current.html)」を参照してください。

## よく読まれるトピック {#section_AFFBC9EDDE5B4E4493A7C2896121A773}

このガイドで人気のトピックは以下になります。

* [はじめに](/help/using/gs/gs.md)
* [ログイン](/help/using/gs/gs-signin.md)
* [役割と権限](/help/using/gs/c-mob-roles-and-permissions.md)
* [モバイル指標](/help/using/gs/metrics/metrics.md)
* [メッセージ](/help/using/in-app-messaging/in-app-messaging.md)
* [獲得](/help/using/acquisition-main/acquisition-main.md)
* [場所](/help/using/location/c-location-overview.md)
* [よくある質問 - Mobile Services](/help/using/faq-mobile.md)

## 開発者

開発者を支援するリンクを次に示します。

* [Mobile SDK およびツールのダウンロード](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md)
* [開発者](https://docs.adobe.com/content/help/ja-JP/analytics/implementation/home.html)

## コミュニティリソース

その他のリソースを次に示します。

* [Experience Cloud フォーラム](https://forums.adobe.com/community/experience-cloud)
* [Adobe Experience Cloud コミュニティ](https://helpx.adobe.com/jp/marketing-cloud.html?promoid=KAWSE)
* [アイデア交換](https://forums.adobe.com/community/experience-cloud/analytics-cloud/analytics)
* [アドビトレーニングおよびチュートリアル](https://helpx.adobe.com/jp/learning.html?promoid=KAUDK)
* [主なソリューションセンター](https://www.adobe.com/jp/marketing-cloud.html)

## SDK ドキュメント {#section_3A500233347C4305AB545E298A827CEA}

ユーザーガイドに加えて、ソフトウェア開発キット（SDK）をダウンロードできます。SDK には、Adobe Mobile でアプリを設定する必要がある設定ファイルの事前入力バージョンを含むカスタマイズされたパッケージが含まれています。

ネイティブライブラリは、次のプラットフォームに対して提供されます。

* [Experience Cloud ソリューション用 Android SDK 4.x](/help/android/overview.md)
* [Experience Cloud ソリューション用 iOS SDK 4.x](/help/ios/overview.md)
* [iOS および Android 4.x SDK 用 Unity プラグイン](/help/unity/get-started.md)
* [Experience Cloud ソリューション 4.x SDK 用 Xamarin コンポーネント](/help/xamarin/get-started.md)
* [Experience Cloud ソリューション用 Universal Windows Platform SDK 4.x](/help/universal-windows/overview.md)
* [Windows 8.1 ユニバーサルアプリストア](/help/windows-appstore/overview.md)

   * [Experience Cloudソリューション4.x SDK 用 Windows Visual Studio Extensions Experience Cloud Solutions 4.x SDK](/help/windows-appstore/extensions/win-vse-4x.md)

* [Experience Cloud ソリューション用 BlackBerry 10 SDK 4](/help/blackberry/overview.md)

## Adobe Mobile の概要に関する Web セミナー {#section_420EA66F39FE44B9B531ADF5F5465543}

*Adobe Mobile の概要に関する Web セミナー*&#x200B;を視聴する（[再生](https://adobe.ly/PsxCFn)）

[  ![](assets/webinar.png) ](https://adobe.ly/PsxCFn)
