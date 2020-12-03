---
description: リストは、モバイルライブラリによって自動的に測定される指標とディメンションです。
keywords: android;library;mobile;sdk
seo-description: リストは、モバイルライブラリによって自動的に測定される指標とディメンションです。
seo-title: ライフサイクル指標
solution: Experience Cloud,Analytics
title: ライフサイクル指標
topic: Developer and implementation
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 83%

---


# ライフサイクル指標 {#lifecycle-metrics}

リストは、モバイルライブラリによって自動的に測定される指標とディメンションです。

詳しくは、「ライフサイクルデータの [トラブルシューティング](https://helpx.adobe.com/jp/analytics/kb/troubleshoot-lifecycle-data.html)」を参照してください。


## ライフサイクル指標およびディメンション {#section_78F036C4296F4BA3A47C2044F79C86C1}

ライフサイクル指標は設定されると、Analytics にはコンテキストデータパラメーターの形で送信され、Target にはパラメーターの形で mbox コールごとに、Audience management へのシグナルとして送信されます。Analytics および Target は同じ形式を使用しますが、Audience management は、各指標に異なるプレフィックスを使用します。

Analyticsでは、各ライフサイクル追跡呼び出しと共に送信されるコンテキストデータは、指標またはディメンションを使用して、自動的に取り込まれ、レポートされます。 例外は内容に記載されています。

## 指標

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

   実行のたびに（クラッシュおよびインストールを含む）トリガーされます。また、ライフサイクルセッションのタイムアウトを超えた場合に、SignatureInfo オブジェクトのバックグラウンドからの再開時にもトリガーされます。

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


## ディメンション

* **インストール日**

   インストール後の初回起動日。日付の形式は `MM/DD/YYYY` です。

   * Analytics コンテキストデータ／Target パラメーター：`a.InstallDate`
   * Audience Manager のシグナル：`c_a_InstallDate`

* **アプリ ID**

   アプリケーションの名前とバージョンを `[AppName] [BundleVersion]` 形式で格納します。例えば、`myapp 1.1` です。

   * Analytics コンテキストデータ／Target パラメーター：`a.AppID`
   * Audience Manager のシグナル：`c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ／Target パラメーター：`a.Launches`
   * Audience Manager のシグナル：`c_a_Launches`

* **初回使用からの日数**

   初回実行時からの日数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceFirstUse`
   * Audience Manager のシグナル：`c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceLastUse`
   * Audience Manager のシグナル：`c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時刻を測定します。この指標では 24 時間形式を使用し、ピーク使用時を調べるための時間分割に使用されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.HourOfDay`
   * Audience Manager のシグナル：`c_a_HourOfDay`

* **曜日**

   アプリが起動された週の曜日の数。

   * Analytics コンテキストデータ／Target パラメーター：`a.DayOfWeek`
   * Audience Manager のシグナル：`c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   OS のバージョン。

   * Analytics コンテキストデータ／Target パラメーター：`a.OSVersion`
   * Audience Manager のシグナル：`c_a_OSVersion`

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.DaysSinceLastUpgrade`
   * Audience Manager のシグナル：`c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.LaunchesSinceUpgrade`
   * Audience Manager のシグナル：`c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.DeviceName`
   * Audience Manager のシグナル：`c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ／Target パラメーター：`a.CarrierName`
   * Audience Manager のシグナル：`c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ／Target パラメーター：`a.Resolution`
   * Audience Manager のシグナル：`c_a_Resolution`


## その他のモバイル指標およびディメンション {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下の指標とディメンションは、モバイルソリューション変数で次の方法によって取り込まれます。

### 指標

* **合計アクション時間**

   `trackTimedAction` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.total`
   * Audience Manager のシグナル：`c_a_action_time_total`

* **アプリでのアクション時間**

   `trackTimedAction` メソッドによって設定されます。
   * Analytics コンテキストデータ／Target パラメーター：`a.action.time.inapp`
   * Audience Manager のシグナル：`c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   `trackLifetimeValue` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター：`a.ltv.amount`
   * Audience Manager のシグナル：`c_a_ltv_amount`

### ディメンション

* **ロケーション（半径 10 km 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analyticsコンテキストデータ/ターゲットパラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager特性：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション（半径 100 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analyticsコンテキストデータ/ターゲットパラメーター：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager特性：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション（半径 1 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analyticsコンテキストデータ/ターゲットパラメーター：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager特性：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   Populated by `trackLocation` methods when device is in a defined POI.

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **目標地点の中心までの距離**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics コンテキストデータ／Target パラメーター：`a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   `trackLifetimeValue` メソッドによって設定されます。

   * Analytics コンテキストデータ／Target パラメーター： `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`
