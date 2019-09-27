---
description: モバイルライブラリによって自動的に測定される指標およびディメンションの一覧を示します。
keywords: android;library;mobile;sdk
seo-description: モバイルライブラリによって自動的に測定される指標およびディメンションの一覧を示します。
seo-title: ライフサイクル指標
solution: Marketing Cloud,Analytics
title: ライフサイクル指標
topic: 開発者と導入
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics{#lifecycle-metrics}

モバイルライブラリによって自動的に測定される指標およびディメンションの一覧を示します。

詳しくは、「ライフサイクルデータのトラブルシ [ューティング」を参照してくださ](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)い。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

設定された場合、ライフサイクル指標は、コンテキストデータパラメーターで Analytics に送信され、mbox 呼び出しのたびにパラメーターで Target に送信され、シグナルとして Audience Manager に送信されます。AnalyticsとTargetは同じ形式を使用し、Audience Managerは指標ごとに異なるプレフィックスを使用します。

Analyticsの場合、各ライフサイクル追跡呼び出しと共に送信されるコンテキストデータは、以下に示す指標またはディメンションを使用して自動的に取得およびレポートされ、例外が記録されます。

### 指標

* **初回起動**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **アップグレード**

   アップグレード後またはバージョン番号の変更時の最初の実行時にトリガーされます。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   >[!TIP]
   >
   >この指標は、Analytics指標に自動的には保存されません。 この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は、Analytics指標に自動的には保存されません。 この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **起動回数**

   クラッシュおよびインストールを含め、実行のたびにトリガーされます。また、ライフサイクルセッションタイムアウトを超えた場合、バックグラウンドからの再開時にもトリガーされます。

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **クラッシュ**

   アプリケーションが終了前にバックグラウンドにならなかった場合にトリガーされます。このイベントは、アプリケーションがクラッシュした後の起動時に送信されます。Adobe Mobile クラッシュレポートには、キャッチできないグローバルな例外ハンドラーは実装されていません。

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **以前のセッションの長さ**

   アプリケーションが開かれ、フォアグラウンドにあった時間に基づいて、以前のアプリケーションセッションが持続した秒数をレポートします。

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### ディメンション

* **インストール日**

   インストール後の初回起動日。日付の形式はです `MM/DD/YYYY`。

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **アプリ ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 例えば、`myapp 1.1` です。

   * Analytics context data/Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics context data/Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **初回使用からの日数**

   初回実行時からの日数。

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時刻を測定します。この指標では 24 時間形式を使用し、ピーク使用時を調べるための時間分割に使用されます。

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **曜日**

   アプリが起動された週の曜日の数。

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   The OS version.

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!IMPORTANT]
   >
   >この指標は、Analytics変数に自動的には保存されません。 レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!IMPORTANT]
   >
   >この指標は、Analytics変数に自動的には保存されません。 レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

The following metrics and dimensions are captured in mobile solution variables by the methods listed in the description.

### 指標

* **合計アクション時間**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.total`
   * Audience Manager trait: `c_a_action_time_total`

* **アプリでのアクション時間**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Audience Manager trait: `c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`

## ディメンション

* **ロケーション (半径 10 km 以内)**

   Populated by `trackLocation` methods.

   * Analyticsコンテキストデータ/Targetパラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Managerの特徴：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション (半径 100 m 以内)**

   Populated by `trackLocation` methods.

   * Analytics context data/Target parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Managerの特徴：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション (半径 1 m 以内)**

   Populated by `trackLocation` methods.

   * Analytics context data/Target parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Managerの特徴：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された POI 内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics context data/Target parameter: `a.loc.poi`
   * Audience Managerの特徴： `c_a_loc_poi`

* **目標地点の中心までの距離**

   デバイスが定義された POI 内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics context data/Target parameter: `a.loc.dist`
   * Audience Managerの特徴： `c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Managerの特徴： `c_a_ltv_amount`
