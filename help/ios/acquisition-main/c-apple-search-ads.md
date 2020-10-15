---
description: Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。
seo-description: Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。
seo-title: Apple Search Ads
solution: Experience Cloud,Analytics
title: Apple Search Ads
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---


# Apple Search Ads {#apple-search-ads}

Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。Search Ads キャンペーンについて詳しくは、[Apple Search Ads](https://searchads.apple.com/jp/) を参照してください。

## メリット {#section_CEA30C652AC8470784B8054E299B80FA}

Apple Ads を使用する利点には以下のものがあります。

* 数行のコードをアプリに追加することによって、Search Ads によるアプリダウンロードキャンペーンの効果を簡単に測定できる。
* 開発者が、ダウンロード日時およびコンバージョンにつながった入札キーワードを利用できる。

## Apple Ads の実装 {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Apple Ads を実装するには、iOS SDK バージョン 4.13.2 以降が必要です。

Search Ads アトリビューションに対してアプリを有効にするには

1. Adobe SDK バージョン 4.13.2 以降を実装します。

   詳しくは、「[コア実装とライフサイクルい](/help/ios/getting-started/dev-qs.md)」を参照してくださ。

1. iAd フレームワークをアプリの Xcode プロジェクトファイルに追加します。

## Search Ads アトリビューションのレポート{#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple Search Ads のアトリビューションデータは、獲得名、ソースおよび項値として提供されます。

   attribution = `true` の場合、すべての `iad-*` フィールドがライフサイクルヒットに含まれます。

   さらに、以下の値が `"iad"` 辞書から一般的な獲得コンテキストデータフィールドにマッピングされます。

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   このマッピングは、標準のレポートで値を使用できるようにします。
