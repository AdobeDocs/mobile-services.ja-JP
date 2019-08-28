---
description: ここでは、デフォルトのモバイル指標およびディメンションに関する参照情報を示します。
keywords: モバイル
seo-description: ここでは、デフォルトのモバイル指標およびディメンションに関する参照情報を示します。
seo-title: モバイル指標およびディメンションのリファレンス
solution: Marketing Cloud、Analytics
title: モバイル指標およびディメンションのリファレンス
topic: 指標
uuid: 96170ae7-8553-4f3e- ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

この情報は、デフォルトのモバイル指標およびディメンションについて理解するのに役立ちます。

>[!TIP]
>
>Adobe Analyticsで設定されるディメンションおよび指標の権限は、Mobile Servicesに適用されます。適切な権限を持たずにレポートを実行しようとすると、エラーが発生します。

## 指標 {#section_6704C815147D44AF96151D626BEB813C}

以下に、デフォルトのモバイル指標のリストを示します。

* **初回起動**

   インストール後または再インストール後の最初の起動時にトリガーされます。

* **アップグレード**

   アップグレード後の最初の起動時またはバージョン番号の変更時にトリガーされます。

* **日別関与ユーザー数**

   特定の日にアプリケーションが使用された場合にトリガーされます。

   >[!TIP]
   >日別関与ユーザーイベントは、Analytics指標に自動的には保存されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

* **月別関与ユーザー数**

   1 ヶ月以内にアプリケーションが使用された場合にトリガーされます。

   >[!TIP]
   >月別関与ユーザーイベントは、Analytics指標に自動的には保存されません。この指標を取得するためのカスタムイベントを設定する処理ルールを作成する必要があります。

* **起動回数**

   インストールとアップグレード以外の起動時にトリガーされます。アプリケーションがバックグラウンドから復帰した場合にもトリガーされます。デフォルトで、アプリがバックグラウンドの状態で 5 分以上経過すると、新規起動がトリガーされます。The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. 詳しくは、"SDK Analyticsオプションの設定»の?«セッションタイムアウト（秒）??**[](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. 詳しくは、[訪問回数とモバイルアプリの起動回数の比較](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html)を参照してください。

* **クラッシュ**

   アプリケーションが正常に終了しなかった場合にトリガーされます。このイベントは、クラッシュ後のアプリケーションの起動時に送信されます。

   >[!TIP]
   >quitが呼び出されないと、アプリケーションがクラッシュすると見なされます。

* **セッションの長さの合計**

   集計されたセッションの長さの合計。

## ディメンション {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

以下に、デフォルトのモバイルディメンションのリストを示します。

* **インストール日**

   インストール後の初回起動日。日付は、*MM/DD/YYYY* の形式です。

* **アプリ ID**

   Stores the Application name and version in the following format: `[AppName] [BundleVersion]`. 例：`myapp 1.1`。

* **起動回数**

   アプリケーションが起動したか、またはバックグラウンドから復帰した回数。

* **初回使用からの日数**

   初回実行時からの日数。

* **前回使用からの日数**

   前回使用時からの経過日数。

* **時刻**

   アプリケーションが起動された時間を測定します。24 時間形式が使用されます。このディメンションは、利用のピーク時間を判定するためにも使用されます。

* **曜日**

   アプリケーションが起動された曜日を表す数値。

* **オペレーティングシステム**

   デバイスのオペレーティングシステム。

* **オペレーティングシステムのバージョン**

   オペレーティングシステムのバージョン。

* **前回アップグレードからの日数**

   アプリのバージョン番号が変更されてからの日数。

   >[!TIP]
   >
   >前回アップグレードからの日数は、Analytics変数に自動的には保存されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

* **前回アップグレードからの起動回数**

   アプリのバージョン番号が変更されてからの起動回数。

   >[!TIP]
   >
   >前回アップグレードからの起動は、Analytics変数に自動的には保存されません。レポート用にこの値を Analytics 変数にコピーする処理ルールを作成する必要があります。

* **デバイス名**

   デバイス名が格納されます。iOSでは、コンマ区切りの2桁の文字列がiOSデバイスを識別します。最初の数字はデバイスの生成を表し、2番目の番号はデバイスファミリーの異なるメンバーを表します。一般的なデバイス名の完全なリストについては、[iOS デバイスのバージョン](/help/ios/reference/device-versions.md)を参照してください。

* **通信事業者名**

   携帯キャリアの名前が格納されます。

* **解像度**

   実際のピクセル単位での幅と高さ。
