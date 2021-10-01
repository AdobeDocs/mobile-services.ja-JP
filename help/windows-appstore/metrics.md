---
description: モバイルライブラリによって自動的に測定される指標とディメンションを示します。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: ライフサイクル指標
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 64%

---

# ライフサイクル指標{#lifecycle-metrics}

モバイルライブラリによって自動的に測定される指標とディメンションを示します。

詳細については、「[ ライフサイクルデータのトラブルシューティング ](https://helpx.adobe.com/jp/analytics/kb/troubleshoot-lifecycle-data.html)」を参照してください。

## ライフサイクル指標およびディメンション {#section_78F036C4296F4BA3A47C2044F79C86C1}

ライフサイクル指標は、設定された場合、Analytics にはコンテキストデータパラメーターの形で、Target にはパラメーターの形で mbox 呼び出しごとに、Audience Managerにはシグナルとして送信されます。 Analytics と Target は同じ形式を使用し、Audience Managerは各指標に異なるプレフィックスを使用します。

Analytics では、各ライフサイクルトラッキングコールと共に送信されるコンテキストデータは、自動的にキャプチャされ、以下に示す指標またはディメンションを使用してレポートされ、例外が記録されます。

### 指標

* **初回起動**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ/Target パラメーター：`a.InstallEvent`
   * Audience Manager のシグナル：`c_a_InstallEvent`

* **アップグレード**

   アップグレード後またはバージョン番号の変更時の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ/Target パラメーター：`a.UpgradeEvent`
   * Audience Manager のシグナル：`c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   >[!TIP]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.DailyEngUserEvent`
   * Audience Manager のシグナル：`c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.MonthlyEngUserEvent`
   * Audience Manager のシグナル：`c_a_MonthlyEngUserEvent`

* **起動回数**

   実行のたびに（クラッシュおよびインストールを含む）トリガーされます。また、ライフサイクルセッションのタイムアウトを超えた場合に、SignatureInfo オブジェクトのバックグラウンドからの再開時にもトリガーされます。

   * Analytics コンテキストデータ/Target パラメーター：`a.LaunchEvent`
   * Audience Manager のシグナル：`c_a_LaunchEvent`

* **クラッシュ**

   アプリケーションが終了前にバックグラウンドにならなかった場合にトリガーされます。このイベントは、アプリケーションがクラッシュした後の起動時に送信されます。Adobe Mobile クラッシュレポートには、キャッチできないグローバルな例外ハンドラーは実装されていません。

   * Analytics コンテキストデータ/Target パラメーター：`a.CrashEvent`
   * Audience Manager のシグナル：`c_a_CrashEvent`

* **以前のセッションの長さ**

   アプリケーションが開かれ、フォアグラウンドにあった時間に基づいて、以前のアプリケーションセッションが持続した秒数をレポートします。

   * Analytics コンテキストデータ/Target パラメーター：`a.PrevSessionLength`
   * Audience Manager のシグナル：`c_a_PrevSessionLength`

### ディメンション

* **インストール日**

   インストール後の初回起動日。日付の形式は `MM/DD/YYYY` です。

   * Analytics コンテキストデータ/Target:`a.InstallDate`
   * Audience Manager：`c_a_InstallDate`

* **アプリ ID**

   アプリケーションの名前とバージョンを `[AppName] [BundleVersion]` 形式で格納します。例えば、`myapp 1.1` です。

   * Analytics コンテキストデータ/Target:`a.AppID`
   * Audience Manager：`c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ/Target:`a.Launches`
   * Audience Manager：`c_a_Launches`

* **初回使用からの日数**

   初回実行時からの日数。

   * Analytics コンテキストデータ/Target:`a.DaysSinceFirstUse`
   * Audience Manager：`c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ/Target:`a.DaysSinceLastUse`
   * Audience Manager：`c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時刻を測定します。この指標では 24 時間形式を使用し、ピーク使用時を調べるための時間分割に使用されます。

   * Analytics コンテキストデータ/Target:`a.HourOfDay`
   * Audience Manager：`c_a_HourOfDay`

* **曜日**

   アプリが起動された週の曜日の数。

   * Analytics コンテキストデータ/Target:`a.DayOfWeek`
   * Audience Manager：`c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   OS のバージョン。

   * Analytics コンテキストデータ/Target:`a.OSVersion`
   * Audience Manager：`c_a_OSVersion`

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target:`a.DaysSinceLastUpgrade`
   * Audience Manager：`c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target:`a.LaunchesSinceUpgrade`
   * Audience Manager：`c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。

   * Analytics コンテキストデータ/Target:`a.DeviceName`
   * Audience Manager：`c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target:`a.CarrierName`
   * Audience Manager：`c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ/Target:`a.Resolution`
   * Audience Manager：`c_a_Resolution`


## その他のモバイル指標およびディメンション {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

次の指標およびディメンションは、説明に記載されているメソッドによってモバイルソリューション変数にキャプチャされます。

### 指標

* **合計アクション時間**

   `trackTimedAction` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.action.time.total`
   * Audience Manager特性：`c_a_action_time_total`

* **アプリでのアクション時間**

   `trackTimedAction` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.action.time.inapp`
   * Audience Manager特性：`c_a_action_time_inapp`

* **ライフタイム値（イベント）**

   `trackLifetimeValue` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.ltv.amount`
   * Audience Manager特性：`c_a_ltv_amount`

## ディメンション

* **ロケーション（半径 10 km 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager特性：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション（半径 100 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager特性：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション（半径 1 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager特性：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された目標地点内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.loc.poi`
   * Audience Manager特性：`c_a_loc_poi`

* **目標地点の中心までの距離**

   デバイスが定義された目標地点内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.loc.dist`
   * Audience Manager特性：`c_a_loc_dist`

* **ライフタイム値（コンバージョン変数）**

   `trackLifetimeValue` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.ltv.amount`
   * Audience Manager特性：`c_a_ltv_amount`
