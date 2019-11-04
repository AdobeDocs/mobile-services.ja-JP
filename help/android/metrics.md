---
description: 以下では、ライフサイクルの実装後にモバイルライブラリによって自動的に測定可能な指標およびディメンションと、ライフサイクルデータのトラブルシューティングに関するページへのリンクを示します。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: 以下では、ライフサイクルの実装後にモバイルライブラリによって自動的に測定可能な指標およびディメンションと、ライフサイクルデータのトラブルシューティングに関するページへのリンクを示します。
seo-title: ライフサイクル指標
solution: Experience Cloud,Analytics
title: ライフサイクル指標
topic: 開発者と導入
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# ライフサイクル指標{#lifecycle-metrics}

この節では、ライフサイクルの実装後にモバイルライブラリによって自動的に測定可能な指標およびディメンションと、ライフサイクルデータのトラブルシューティングに関するページへのリンクに関する情報を提供します。トラブルシューティングの詳細については、「[ライフサイクルデータのトラブルシューティング](https://helpx.adobe.com/jp/analytics/kb/troubleshoot-lifecycle-data.html)」を参照してください。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## ライフサイクル指標およびディメンション {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定された場合、ライフサイクル指標は、コンテキストデータパラメーターで Analytics に送信され、mbox 呼び出しのたびにパラメーターで Target に送信され、シグナルとして Audience Management に送信されます。Analytics および Target は同じ形式を使用しますが、Audience Management は、各指標に異なるプレフィックスを使用します。

Analytics の場合、各ライフサイクルトラッキングコールとともに送信されるコンテキストデータは、自動的にキャプチャされ、先頭の列の指標またはディメンションを使用してレポートされ、例外が指摘されます。

### 指標

* **初回起動**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.InstallEvent`
   * Audience Manager のシグナル：`c_a_InstallEvent`

* **アップグレード**

   アップグレード後またはバージョン番号の変更時の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ／Target パラメーター：`a.UpgradeEvent`
   * Audience Manager のシグナル：`c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.DailyEngUserEvent`
   * Audience Manager のシグナル：`c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.MonthlyEngUserEvent`
   * Audience Manager のシグナル：`c_a_MonthlyEngUserEvent`

* **起動回数**

   クラッシュおよびインストールを含め、実行のたびにトリガーされます。また、ライフサイクルセッションタイムアウトを超えた場合、バックグラウンドからの再開時にもトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.LaunchEvent`
   * Audience Manager のシグナル：`c_a_LaunchEvent`

* **クラッシュ**

   アプリケーションが終了前にバックグラウンドにならなかった場合にトリガーされます。このイベントは、アプリケーションがクラッシュした後の起動時に送信されます。Adobe Mobile クラッシュレポートには、キャッチできないグローバルな例外ハンドラーは実装されていません。

   * Analytics コンテキストデータ／Target パラメーター：`a.CrashEvent`
   * Audience Manager のシグナル：`c_a_CrashEvent`

* **以前のセッションの長さ**

   アプリケーションが開かれ、フォアグラウンドにあった時間に基づいて、以前のアプリケーションセッションが持続した秒数をレポートします。

   * Analytics コンテキストデータ／Target パラメーター：`a.PrevSessionLength`
   * Audience Manager のシグナル：`c_a_PrevSessionLength`


### ディメンション

* **インストール日**

   インストール後の初回起動日。日付フォーマットは MM/DD/YYYY です。

   * Analytics コンテキストデータ／Target パラメーター：`a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **アプリ ID**

   アプリケーションの名前とバージョンを `[AppName] [BundleVersion]` 形式で格納します。例えば、`myapp 1.1` です。

   * Analytics コンテキストデータ／Target パラメーター：`a.AppID`
   * Audience Manager: `c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ／Target パラメーター：`a.Launches`
   * Audience Manager: `c_a_Launches`

* **初回使用からの日数**

   初回実行時からの日数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時刻を測定します。この指標では 24 時間形式を使用し、ピーク使用時を調べるための時間分割に使用されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **曜日**

   アプリが起動された週の曜日の数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   OS のバージョン。

   * Analytics コンテキストデータ／Target パラメーター：`a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。重要：この指標は Analytics 変数に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ／Target パラメーター：`a.Resolution`
   * Audience Manager: `c_a_Resolution`

## その他のモバイル指標およびディメンション {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

次の指標およびディメンションは、**説明**&#x200B;列にリストされているメソッドによってモバイルソリューション変数にキャプチャされます。

### 指標

* **合計アクション時間**

   `trackTimedAction` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.total`
   * Audience Managerの特性：`c_a_action_time_total`

* **アプリでのアクション時間**

   `trackTimedAction` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.inapp`
   * Audience Managerの特性：`c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   `trackLifetimeValue` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.ltv.amount`
   * Audience Managerの特性：`c_a_ltv_amount`

### ディメンション

* **ロケーション（半径 10 km 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Managerの特性：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション（半径 100 m 以内）**

   trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Managerの特性：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション（半径 1 m 以内）**

   trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Managerの特性：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された POI 内にある場合に trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.poi`
   * Audience Managerの特性：`c_a_loc_poi`

* **目標地点の中心までの距離**

   デバイスが定義された POI 内にある場合に trackLocation メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.dist`
   * Audience Managerの特性：`c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   trackLifetimeValue メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.ltv.amount`
   * Audience Managerの特性：`c_a_ltv_amount`

* **トラッキングコード**

   モバイルアプリの獲得によって設定され、Adobe Mobile Services によって自動的に生成されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.trackingcode`
   * Audience Managerの特性：`c_a_referrer_campaign_trackingcode`

* **Campaign**

   キャンペーンの名前。キャンペーン変数にも格納されます。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.name`
   * Audience Managerの特性：`c_a_referrer_campaign_name`

* **キャンペーンの内容**

   リンクを表示するコンテンツの名前または ID。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.content`
   * Audience Managerの特性：`c_a_referrer_campaign_content`

* **キャンペーンのメディア**

   バナーまたは電子メールなどのマーケティングメディア。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.medium`
   * Audience Managerの特性：`c_a_referrer_campaign_medium`

* **キャンペーンのソース**

   ニュースレターやソーシャルメディアネットワークなどのオリジナルリファラー。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.source`
   * Audience Managerの特性：`c_a_referrer_campaign_source`

* **キャンペーンのキーワード**

   この獲得で追跡する有料検索キーワードまたはその他の用語。モバイルアプリの獲得によって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.referrer.campaign.term`
   * Audience Managerの特性：`c_a_referrer_campaign_term`
