---
description: 以下の表に、ライフサイクル実装後にモバイルライブラリで自動的に測定できる指標とディメンションの一覧を示します。
seo-description: 以下の表に、ライフサイクル実装後にモバイルライブラリで自動的に測定できる指標とディメンションの一覧を示します。
seo-title: ライフサイクル指標
solution: Marketing Cloud,Analytics
title: ライフサイクル指標
topic: 開発者と導入
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# Lifecycle metrics {#lifecycle-metrics}

Here are the metrics and dimensions that can be automatically measured by the mobile library after lifecycle is implemented.

## 新しいAdobe Experience Platform Mobile SDKリリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* To get started, go to [Experience Platform Launch](https://launch.adobe.com/).
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

ライフサイクル指標が設定された後、それらの指標は、Analytics にはコンテキストデータパラメーターの形で送信され、Target にはパラメーターの形で mbox コールごとに送信され、Audience Manager にはシグナルとして送信されます。Analytics および Target は同じ形式を使用しますが、Audience Manager は、各指標に異なるプレフィックスを使用します。

Analytics の場合、各ライフサイクルトラッキングコールとともに送信されるコンテキストデータは、自動的にキャプチャされ、先頭の列の指標またはディメンションを使用してレポートされます。

>[!TIP]
>
>例外は説明に記載されています。

### 指標

* **初回起動**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **アップグレード**

   アップグレード後の最初の起動時、またはバージョン番号の変更時に常にトリガーされます。

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **起動回数**

   クラッシュおよびインストールを含め、実行のたびにトリガーされます。ライフサイクルセッションのタイムアウトを超えた後にアプリがバックグラウンドから再開されたときにもトリガーされます。

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **クラッシュ**

   終了する前にアプリケーションがバックグラウンドに移行されていない場合にトリガーされます。このイベントは、クラッシュ後にアプリケーションが再開されたときに送信されます。Adobe Mobile クラッシュレポートには、キャッチできないグローバルな例外ハンドラーは実装されていません。

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **以前のセッションの長さ**

   アプリケーションが開かれ、フォアグラウンドにあった時間に基づいて、以前のアプリケーションセッションが持続した秒数をレポートします。

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> 日別関与 *ユーザー指標と月別関* 与ユーザー指標は ** 、Analytics指標に自動的には保存されません。 You must create a processing rule that sets a custom event to capture these metrics.

#### ディメンション

* **インストール日**

   インストール後の初回起動日。日付の形式はです `MM/DD/YYYY`。

   * Analytics コンテキストデータ／Target: `a.InstallDate`
   * Audience Management: `c_a_InstallDate`

* **アプリ ID**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. 例：`myapp 1.1`。

   * Analytics コンテキストデータ／Target: `a.AppID`
   * Audience Management: `c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ／Target: `a.Launches`
   * Audience Management: `c_a_Launches`

* **初回使用からの日数**

   初回起動時からの日数。

   * Analytics コンテキストデータ／Target: `a.DaysSinceFirstUse`
   * Audience Management: `c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ／Target: `a.DaysSinceLastUse`
   * Audience Management: `c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時間帯を測定します。24 時間形式が使用されます。利用のピーク時間を判定するために使用します。

   * Analytics コンテキストデータ／Target: `a.HourOfDay`
   * Audience Management: `c_a_HourOfDay`

* **曜日**

   アプリケーションが起動された曜日を表す数値。

   * Analytics コンテキストデータ／Target: `a.DayOfWeek`
   * Audience Management: `c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   アプリのバージョン番号が変更されてからの日数。

   * Analytics コンテキストデータ／Target: `a.OSVersion`
   * Audience Management: `c_a_OSVersion|OS version`

* **前回アップグレードからの日数**

   前回アップグレードからの日数.

   * Analytics コンテキストデータ／Target: `a.DaysSinceLastUpgrade`
   * Audience Management: `c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   * Analytics コンテキストデータ／Target: `a.LaunchesSinceUpgrade`
   * Audience Management: `c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。iOS デバイスを識別するコンマ区切りの 2 桁の文字列。最初の番号は通常、デバイスの世代を表します。次の番号は通常、デバイスファミリー内の個々のメンバーのバージョン番号です。一般的なデバイス名の一覧は、  iOS デバイスのバージョン.

   * Analytics コンテキストデータ／Target: `a.DeviceName`
   * Audience Management: `c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   * Analytics コンテキストデータ／Target: `a.CarrierName`
   * Audience Management: `c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ／Target: `a.Resolution`
   * Audience Management: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >前回ア *ップグレードからの日数*、前回ア *ップグレードからの起動回数*、通信事業者名 *(Carrier Name* )ディメンションは、Analytics変数に自動的には保存されません。 You must create a processing rule to copy the values to an Analytics variable for reporting.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下の指標とディメンションは、モバイルソリューション変数で、リストに示した方法で取り込まれます。

### 指標

* **合計アクション時間**

   trackTimedAction メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **アプリでのアクション時間**

   trackTimedAction メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   trackLifetimeValue メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### ディメンション

* **ロケーション (半径 10 km 以内)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Targetパラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Managementの特徴：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション (半径 100 m 以内)**

   trackLocation メソッドによって設定されます。

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management trait:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション (半径 1 m 以内)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Managementの特徴：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された目標地点内に入ると、trackLocation メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **目標地点の中心までの距離**

   デバイスが定義された目標地点内に入ると、trackLocation メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   trackLifetimeValue メソッドによって設定されます。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **トラッキングコード**

   モバイルアプリの獲得によって設定されます。Adobe Mobile Services によって自動的に生成されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   キャンペーンの名前。キャンペーン変数にも格納されます。モバイルアプリケーションの獲得によって設定されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **キャンペーンの内容**

   リンクを表示するコンテンツの名前または ID。モバイルアプリの獲得によって設定されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **キャンペーンのメディア**

   バナーや電子メールなどのマーケティングメディア。モバイルアプリの獲得によって設定されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **キャンペーンのソース**

   ニュースレターやソーシャルメディアネットワークなどのオリジナルリファラー。モバイルアプリケーションの獲得によって設定されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **キャンペーンのキーワード**

   この獲得で追跡する有料検索キーワードやその他の語句。モバイルアプリケーションの獲得によって設定されます。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
