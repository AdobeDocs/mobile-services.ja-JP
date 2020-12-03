---
description: 以下の表に、ライフサイクルを実装した後、モバイルアリブラリで自動的に測定可能な指標とディメンションを示します。
seo-description: 以下の表に、ライフサイクルを実装した後、モバイルアリブラリで自動的に測定可能な指標とディメンションを示します。
seo-title: ライフサイクル指標
solution: Experience Cloud,Analytics
title: ライフサイクル指標
topic: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 100%

---


# ライフサイクル指標 {#lifecycle-metrics}

ライフサイクル実装後にモバイルライブラリで自動的に測定できる指標とディメンションの一覧を示します。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、[Experience Platform Launch](https://launch.adobe.com/) に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。


## ライフサイクル指標およびディメンション {#section_78F036C4296F4BA3A47C2044F79C86C1}

ライフサイクル指標が設定された後、それらの指標は、Analytics にはコンテキストデータパラメーターの形で送信され、Target にはパラメーターの形で mbox コールごとに送信され、Audience Manager にはシグナルとして送信されます。Analytics および Target は同じ形式を使用しますが、Audience Manager は、各指標に異なるプレフィックスを使用します。

Analytics の場合、各ライフサイクルトラッキングコールとともに送信されるコンテキストデータは、自動的にキャプチャされ、先頭の列の指標またはディメンションを使用してレポートされます。

>[!TIP]
>
>例外は説明に記載されています。

### 指標

* **初回起動**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.InstallEvent`
   * Audience Manager のシグナル：`c_a_InstallEvent`

* **アップグレード**

   アップグレード後の最初の起動時、またはバージョン番号の変更時に常にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.UpgradeEvent`
   * Audience Manager のシグナル：`c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.DailyEngUserEvent`
   * Audience Manager のシグナル：`c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.MonthlyEngUserEvent`
   * Audience Manager のシグナル：`c_a_MonthlyEngUserEvent`

* **起動回数**

   クラッシュおよびインストールを含め、実行のたびにトリガーされます。また、ライフサイクルセッションのタイムアウトを超えた後に、アプリがバックグラウンドから再開された場合にもトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.LaunchEvent`
   * Audience Manager のシグナル：`c_a_LaunchEvent`

* **クラッシュ**

   終了する前にアプリケーションがバックグラウンドに移行されていない場合にトリガーされます。このイベントは、クラッシュ後にアプリケーションが再開されたときに送信されます。Adobe Mobile クラッシュレポートには、キャッチできないグローバルな例外ハンドラーは実装されていません。

   * Analytics コンテキストデータ／Target パラメーター：`a.CrashEvent`
   * Audience Manager のシグナル：`c_a_CrashEvent`

* **以前のセッションの長さ**

   アプリケーションが開かれ、フォアグラウンドにあった時間に基づいて、以前のアプリケーションセッションが持続した秒数をレポートします。

   * Analytics コンテキストデータ／Target パラメーター：`a.PrevSessionLength`
   * Audience Manager のシグナル：`c_a_PrevSessionLength`

>[!IMPORTANT]
>
> *日別関与ユーザー数*&#x200B;および&#x200B;*月別関与ユーザー数*&#x200B;指標は、Analytics 指標に自動的には追加されません。これらの指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

#### ディメンション

* **インストール日**

   インストール後の初回起動日。日付の形式は `MM/DD/YYYY` です。

   * Analytics コンテキストデータ／Target：`a.InstallDate`
   * Audience Management：`c_a_InstallDate`

* **アプリ ID**

   アプリケーションの名前とバージョンを `[AppName] [BundleVersion]` 形式で格納します。例：`myapp 1.1`。

   * Analytics コンテキストデータ／Target：`a.AppID`
   * Audience Management：`c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ／Target：`a.Launches`
   * Audience Management：`c_a_Launches`

* **初回使用からの日数**

   初回起動時からの日数。

   * Analytics コンテキストデータ／Target：`a.DaysSinceFirstUse`
   * Audience Management：`c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ／Target：`a.DaysSinceLastUse`
   * Audience Management：`c_a_DaysSinceLastUse`

* **時刻**

   アプリケーションが起動された時間を測定します。24 時間形式が使用されます。利用のピーク時間を判定するために使用します。

   * Analytics コンテキストデータ／Target：`a.HourOfDay`
   * Audience Management：`c_a_HourOfDay`

* **曜日**

   アプリケーションが起動された曜日を表す数値。

   * Analytics コンテキストデータ／Target：`a.DayOfWeek`
   * Audience Management：`c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   アプリのバージョン番号が変更されてからの日数。

   * Analytics コンテキストデータ／Target：`a.OSVersion`
   * Audience Management：`c_a_OSVersion|OS version`

* **前回アップグレードからの日数**

   前回アップグレードからの日数。

   * Analytics コンテキストデータ／Target：`a.DaysSinceLastUpgrade`
   * Audience Management：`c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   * Analytics コンテキストデータ／Target：`a.LaunchesSinceUpgrade`
   * Audience Management：`c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。iOS デバイスを識別するコンマ区切りの 2 桁の文字列。最初の番号は通常、デバイスの世代を表します。次の番号は通常、デバイスファミリー内の個々のメンバーのバージョン番号です。一般的なデバイス名の一覧は、  iOS デバイスのバージョンを参照してください。

   * Analytics コンテキストデータ／Target：`a.DeviceName`
   * Audience Management：`c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   * Analytics コンテキストデータ／Target：`a.CarrierName`
   * Audience Management：`c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ／Target：`a.Resolution`
   * Audience Management：`c_a_Resolution`
   >[!IMPORTANT]
   >
   >*前回アップグレードからの日数*、*前回アップグレードからの起動回数*、および&#x200B;*通信事業者名*&#x200B;ディメンションは、Analytics 変数に自動的には保存されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。


## その他のモバイル指標およびディメンション {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

次の指標およびディメンションは、リストされているメソッドによってモバイルソリューション変数にキャプチャされます。

### 指標

* **合計アクション時間**

   trackTimedAction メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.total`
   * Audience Management の特性：`c_a_action_time_total`

* **アプリでのアクション時間**

   trackTimedAction メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.inapp`
   * Audience Management の特性：`c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   trackLifetimeValue メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.ltv.amount`
   * Audience Management の特性：`c_a_ltv_amount`


### ディメンション

* **ロケーション（半径 10 km 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management の特性：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション（半径 100 m 以内）**

   trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management の特性：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション（半径 1 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Management の特性：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された目標地点内に入ると、trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.poi`
   * Audience Management の特性：`c_a_loc_poi`

* **目標地点の中心までの距離**

   デバイスが定義された目標地点内に入ると、trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.dist`
   * Audience Management の特性：`c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   trackLifetimeValue メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.ltv.amount`
   * Audience Management の特性：`c_a_ltv_amount`

* **トラッキングコード**

   モバイルアプリの獲得によって設定されます。Adobe Mobile Services によって自動的に生成されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.trackingcode`
   * Audience Management の特性：`c_a_referrer_campaign_trackingcode`

* **Campaign**

   キャンペーンの名前。キャンペーン変数にも格納されます。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.name`
   * Audience Management の特性：`c_a_referrer_campaign_name`

* **キャンペーンの内容**

   リンクを表示したコンテンツの名前または ID。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.content`
   * Audience Management の特性：`c_a_referrer_campaign_content`

* **キャンペーンのメディア**

   マーケティングメディア（バナー、電子メールなど）。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.medium`
   * Audience Management の特性：`c_a_referrer_campaign_medium`

* **キャンペーンのソース**

   オリジナルリファラー（ニュースレターやソーシャルメディアネットワークなど）。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.source`
   * Audience Management の特性：`c_a_referrer_campaign_source`

* **キャンペーンのキーワード**

   この獲得で追跡する有料キーワードまたはその他の用語。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.term`
   * Audience Management の特性：`c_a_referrer_campaign_term`
