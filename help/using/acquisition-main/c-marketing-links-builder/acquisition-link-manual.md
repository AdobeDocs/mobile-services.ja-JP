---
description: URL パラメーターを手作業で設定することで、新しいモバイルアプリユーザーをその場で獲得するためのマーケティングリンクを作成できます。
keywords: モバイル
seo-description: URL パラメーターを手作業で設定することで、新しいモバイルアプリユーザーをその場で獲得するためのマーケティングリンクを作成できます。
seo-title: ダウンロード計測用リンクの手動作成
solution: Experience Cloud,Analytics
title: ダウンロード計測用リンクの手動作成
topic-fix: Metrics
uuid: d7709203-f793-4982-adaa-9c3c914aca2b
exl-id: aef9fe3e-32dc-4ec0-9eda-f64cc5e486a3
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---

# ダウンロード計測用リンクの手動作成 {#create-acquisition-link-manually}

URL パラメーターを手作業で設定することで、新しいモバイルアプリユーザーをその場で獲得するためのマーケティングリンクを作成できます。

>[!IMPORTANT]
>
>この機能には、SDK バージョン 4.6 以降が必要です。詳しくは、「[獲得の前提条件](/help/using/acquisition-main/c-acquisition-prerequisites.md)」を参照してください。

次の図は、手動で作成したトラッキングリンクのコンポーネント、およびダウンロード計測用リンクを手作業で作成する場合に適切に設定する必要がある様々な URL パラメーターの例を示しています。

![](assets/acquisition_url.png)

このリンクは、モバイルアプリで、Google Play ストアまたは Apple App Store へのプラットフォーム固有のリダイレクトを実行するように設定されます。宛先が判断できない場合、デフォルトのストアは Apple App Store に設定されています。アプリがインストールされた後、Analytics のインストールヒットにカスタムコンテキストキー `my.custom.key:test` が追加されます。

リンクを手動で作成するには、次の URL 形式を使用します。

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>使用している Android SDK のバージョンは、これには影響しません。

iOS の場合、次の正しいプロトコルを使用していることを確認します。

* バージョン 4.7.0 より前の iOS SDK を使用している場合、または iOS SDK 4.7.0 以降を使用していて、アプリ設定ページで **HTTPS を使用** が選択されて&#x200B;**[!UICONTROL いない]**&#x200B;場合は、**HTTP** を選択します。
* iOS SDK 4.7.0 以降を使用していて、「アプリ設定の管理」ページで「**[!UICONTROL HTTPS を使用]**」が選択されて&#x200B;**いる**&#x200B;場合は、**HTTPS** を使用します。

ここでは、次の条件が当てはまります。

* `{mobile-services-app-hash}`は、構成 `acquisition:appid ` ファイル内でのアプリケーション識別子を照合します。

   `{mobile-services-app-hash}` は、アプリ設定ページ、「SDK の獲得オプション」の「トラッキング ID」フィールドにあります。

   ![](assets/tracking-id.png)

* `{parameters}` は、具体的な名前を指定した標準 URL クエリーパラメーターのリストです。

次にパラメーターのリストを示します。

* **`a_g_id`**

   Google Play ストアのアプリ識別子。

   * サンプル値：`com.adobe.beardcons`

* **`a_g_lo`**

   Google Play ストアのロケールの上書き。

   * サンプル値：`ko`

* **`a_i_id`**

   iTunes Store のアプリ識別子。

   * サンプル値：`835196493`

* **`a_i_lo`**

   iTunes Store のロケールの上書き。

   * サンプル値：`jp`

* **`a_dd`**

   自動リダイレクトのデフォルトのストア。

   * サンプル値：`i | g`

* **`a_cid`**

   カスタムの ID の上書き（通常、iOS では IDFA、Android では ADID）。

   * サンプル値：`Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   プレフィックス `ctx` が付加されているキーは、結果として生成される起動ヒットのコンテキストデータとなります。

   * サンプル値：`ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   獲得キャンペーン名。

   このパラメーターは、様々なダウンロード計測用リンクのパフォーマンスを比較する場合のレポートに必要です。

   * サンプル値：2015 年サミット会議

* **`ctxa.referrer.campaign.trackingcode`**

   トラッキングコード

   このパラメーターは、様々なダウンロード計測用リンクのパフォーマンスを比較する場合のレポートに必要です。

   * サンプル値：`lexsxouj`

* **`ctxa.referrer.campaign.source`**

   ソース。

   * サンプル値：広告ネットワーク

* **`ctxa.referrer.campaign.medium`**

   メディア

   * サンプル値：電子メール

* **`ctxa.referrer.campaign.content`**

   コンテンツ

   * サンプル値：画像# 325689

* **`ctxa.referrer.campaign.term`**

   用語

   * サンプル値：ハイキング + ブーツ


ダウンロード計測用リンクを手動で作成する場合は、次の情報に注意してください。

* この表に記載されていないすべてのパラメーターは、アプリストアのリダイレクトの一部として渡されます。
* すべてのパラメーターは、技術的にはオプションです。ただし、少なくとも 1 つのストア ID が指定されていない場合、リンクは機能しなくなります。

   ストア ID の例として、`a_i_id`／`a_g_id` があります。

* 宛先のストアを自動的に判定できず、デフォルトも指定されていない場合は、404 エラーが返されます。
