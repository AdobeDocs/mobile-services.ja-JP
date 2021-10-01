---
description: 以下では、ライフサイクルの実装後にモバイルライブラリによって自動的に測定可能な指標およびディメンションと、ライフサイクルデータのトラブルシューティングに関するページへのリンクを示します。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: ライフサイクル指標
topic-fix: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
exl-id: d7436411-65bd-4cf7-ae3e-cec829a7690a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 78%

---

# ライフサイクル指標 {#lifecycle-metrics}

以下では、ライフサイクルの実装後にモバイルライブラリによって自動的に測定可能な指標およびディメンションと、ライフサイクルデータのトラブルシューティングに関するページへのリンクを示します。

詳細については、ナレッジベース（[ ライフサイクルデータのトラブルシューティング ](https://helpx.adobe.com/jp/analytics/kb/troubleshoot-lifecycle-data.html)）を参照してください。

## ライフサイクル指標およびディメンション {#section_78F036C4296F4BA3A47C2044F79C86C1}

ライフサイクル指標は設定されると、Analytics にはコンテキストデータパラメーターの形で送信され、Target にはパラメーターの形で mbox コールごとに、Audience management へのシグナルとして送信されます。Analytics および Target は同じ形式を使用しますが、Audience management は、各指標に異なるプレフィックスを使用します。

Analytics の場合、各ライフサイクルトラッキングコールと共に送信されるコンテキストデータは、自動的にキャプチャされ、指標またはディメンションを使用してレポートされます。

### 指標

* **a.media.name**

   インストール後または再インストール後の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ/Target パラメーター：`a.InstallEvent`
   * Audience Manager のシグナル：`c_a_InstallEvent`

* **アップグレード**

   アップグレード後またはバージョン番号の変更時の最初の実行時にトリガーされます。

   * Analytics コンテキストデータ/Target パラメーター：`a.UpgradeEvent`
   * Audience Manager のシグナル：`c_a_UpgradeEvent`

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.DailyEngUserEvent`
   * Audience Manager のシグナル：`c_a_DailyEngUserEvent`

* **月別関与ユーザー数**

   特定の月内にアプリケーションが使用された場合にトリガーされます。>>>>

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

   * Analytics コンテキストデータ/Target パラメーター：`a.InstallDate`
   * Audience Manager のシグナル：`c_a_InstallDate`

* **アプリ ID**

   アプリケーションの名前とバージョンを次の形式で格納します。 
   `[AppName] [BundleVersion]`。

   例えば、`myapp 1.1` です。

   * Analytics コンテキストデータ/Target パラメーター：`a.AppID`
   * Audience Manager のシグナル：`c_a_AppID`

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

   * Analytics コンテキストデータ/Target パラメーター：`a.Launches`
   * Audience Manager のシグナル：`c_a_Launches`

* **初回使用からの日数**

   初回実行時からの日数。

   * Analytics コンテキストデータ/Target パラメーター：`a.DaysSinceFirstUse`
   * Audience Manager のシグナル：`c_a_DaysSinceFirstUse`

* **前回使用からの日数**

   前回使用時からの経過日数。

   * Analytics コンテキストデータ/Target パラメーター：`a.DaysSinceLastUse`
   * Audience Manager のシグナル：`c_a_DaysSinceLastUse`

* **時刻**

   アプリが起動された時刻を測定します。この指標では 24 時間形式を使用し、ピーク使用時を調べるための時間分割に使用されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.HourOfDay`
   * Audience Manager のシグナル：`c_a_HourOfDay`

* **曜日**

   アプリが起動された週の曜日の数。

   * Analytics コンテキストデータ/Target パラメーター：`a.DayOfWeek`
   * Audience Manager のシグナル：`c_a_DayOfWeek`

* **オペレーティングシステムのバージョン**

   OS のバージョン。

   * Analytics コンテキストデータ/Target パラメーター：`a.OSVersion`
   * Audience Manager のシグナル：`c_a_OSVersion`

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.DaysSinceLastUpgrade`
   * Audience Manager のシグナル：`c_a_DaysSinceLastUpgrade`

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.LaunchesSinceUpgrade`
   * Audience Manager のシグナル：`c_a_LaunchesSinceUpgrade`

* **デバイス名**

   デバイス名が格納されます。

   * Analytics コンテキストデータ/Target パラメーター：`a.DeviceName`
   * Audience Manager のシグナル：`c_a_DeviceName`

* **通信事業者名**

   デバイスによって提供された携帯キャリアの名前が格納されます。

   >[!IMPORTANT]
   >
   >この指標は Analytics 指標に自動的には格納されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

   * Analytics コンテキストデータ/Target パラメーター：`a.CarrierName`
   * Audience Manager のシグナル：`c_a_CarrierName`

* **解像度**

   実際のピクセル単位での幅 x 高さ。

   * Analytics コンテキストデータ/Target パラメーター：`a.Resolution`
   * Audience Manager のシグナル：`c_a_Resolution`

## その他のモバイル指標およびディメンション {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

次の指標およびディメンションは、リストされているメソッドによってモバイルソリューション変数にキャプチャされます。

* **ロケーション（半径 10 km 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management の特性：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **ロケーション（半径 100 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management の特性：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **ロケーション（半径 1 m 以内）**

   `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Management の特性：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目標点名**

   デバイスが定義された目標地点内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.poi`
   * Audience Management の特性：

      * `c_a_loc_poi`


* **目標地点の中心までの距離**

   デバイスが定義された目標地点内にある場合に `trackLocation` メソッドによって設定されます。

   * Analytics コンテキストデータ/Target パラメーター：

      * `a.loc.dist`
   * Audience Management の特性：

      * `c_a_loc_dist`
