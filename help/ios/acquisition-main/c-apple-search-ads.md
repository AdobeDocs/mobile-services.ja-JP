---
description: Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。
seo-description: Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。
seo-title: Apple Search Ads
solution: Marketing Cloud、Analytics
title: Apple Search Ads
topic: 開発者と導入
uuid: 790080e8-067e-4bfd- a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: 9c6923d14d1a5f30e5873299def61b0734e52429

---


# Apple Search Ads {#apple-search-ads}

Adobe SDK は、Apple Search Ads アプリのアトリビューション API を利用して、開発者とマーケターが Apple App Store の Search Ads キャンペーンからのアプリのダウンロード数を追跡し、アトリビューションをおこなえるようにします。Search Ads キャンペーンについて詳しくは、[Apple Search Ads](https://searchads.apple.com) を参照してください。

## メリット {#section_CEA30C652AC8470784B8054E299B80FA}

Apple Ads を使用する利点には以下のものがあります。

* 数行のコードをアプリに追加することによって、Search Ads によるアプリダウンロードキャンペーンの効果を簡単に測定できる。
* 開発者が、ダウンロード日時およびコンバージョンにつながった入札キーワードを利用できる。

## Apple Ads の実装 {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Apple広告を実装するには、iOS SDKバージョン4.13.2以降が必要です。

Search Ads アトリビューションに対してアプリを有効にするには

1. Adobe SDK バージョン 4.13.2 以降を実装します。

   詳しくは、[コアの実装とライフサイクル](/help/ios/getting-started/dev-qs.md)。

1. iAd フレームワークをアプリの Xcode プロジェクトファイルに追加します。

## Search Ads アトリビューションのレポート {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple Search Ads のアトリビューションデータは、獲得名、ソースおよび項値として提供されます。

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   さらに、以下の値が "`iad`" 辞書から一般的な獲得コンテキストデータフィールドにマッピングされます。

   * " `iad-campaign-id`" --&gt; " `a.referrer.campaign.trackingcode`"
   * " `iad-campaign-name`" --&gt;" `a.referrer.campaign.name``"
   * " `iad-adgroup-id`" --&gt; " `a.referrer.campaign.content`"
   * " `iad-keyword`" --&gt; " `a.referrer.campaign.term`"
   このマッピングによって、標準のレポートで値を使用できるようになります。

