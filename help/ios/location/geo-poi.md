---
description: 位置情報を利用すると、緯度と経度およびアプリ内にあらかじめ定義されている目標地点を用いてロケーションデータを測定することができます。
seo-description: 位置情報を利用すると、緯度と経度およびアプリ内にあらかじめ定義されている目標地点を用いてロケーションデータを測定することができます。
seo-title: 位置情報と目標地点
solution: Marketing Cloud、Analytics
title: 位置情報と目標地点
topic: 開発者と導入
uuid: c800ec85- a33f-425d- b28f- bfe8bf229ae8
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

位置情報を利用すると、緯度と経度およびアプリ内にあらかじめ定義されている目標地点を用いてロケーションデータを測定することができます。

各 `trackLocation` コールが以下の情報を送信します。

* 緯度、経度および Adobe Mobile Services で定義されている目標地点（POI）のロケーション。

   この情報がモバイルソリューション変数に渡され、自動的にレポートが作成されます。

* コンテキストデータとして渡された中心からの距離と精度。

   これらの変数は、自動ではキャプチャされません。You must map these context data variables by using the instructions in *Sending Additional Data* section below.

## POI の動的更新 {#section_3747B310DD5147E2AAE915E762997712}

バージョン 4.2 以降、POI は Adobe Mobile インターフェイスで定義され、アプリ設定ファイルに動的に同期されます。This synchronization requires an `analytics.poi` setting in the `ADBMobile.json` file:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

詳しくは [、ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)を参照してください。

この設定がない場合は、更新されたバージョンの `ADBMobile.json` ファイルをダウンロードして、アプリに追加する必要があります。詳しくは、「開始する前にSDKおよびテストツールを *ダウンロードする」* を参照 [](/help/ios/getting-started/requirements.md)してください。

## 地域の位置とPOISの追跡 {#section_B1616E400A7548F9A672F97FEC75AE27}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackLocation` を呼び出して、現在の位置を追跡します。

   ```objective-c
   CLLocation *currentLocation = location; 
   [ADBMobile trackLocation: currentLocation data: nil]; 
   ```

   >[!TIP]
   >
   >いつ `trackLocation` でも呼び出すことができます。

   `trackLocation` 呼び出しに渡される場所を決定するには、「ユーザーの場所 [を取得する」を使用](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html)します。

さらに、ロケーションが定義済みの POI 半径内にあると判断された場合は、`a.loc.poi` コンテキストデータ変数が `trackLocation` ヒットとともに送信され、ロケーションレポートに POI としてレポートされます。`a.loc.dist` コンテキスト変数も、定義された座標からの距離（メートル単位）と共に送信されます。

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

位置データに加えて、各位置追跡呼び出しで追加のコンテキストデータを送信することができます。

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

コンテキストデータ値は、カスタム変数にマップする必要があります。

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

緯度と経度はそれぞれ 3 種類のコンテキストデータパラメーターを使用して送信されます。各パラメーターは、6 つのコンテキストデータパラメーターの合計に対して、様々な精度を表します。

例えば、座標の緯度 = 40.93231、経度 = -111.93152 は、精度 1 m のロケーションを表します。この位置は、次の変数に応じて様々なレベルの精度に分割されます。

* `a.loc.lat.a`= 040.9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111.9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

一部の精度は、現在のロケーションの正確さに応じて、「00」と表示されることがあります。例えば、ロケーションの現在の精度が 100 m の場合、`a.loc.lat.c` および `a.loc.lon.c` は「00」と設定されます。

## 追加情報 {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

次の情報に留意してください。

* `trackLocation` リクエストは `trackAction` 、呼び出しと同等に送信されます。

* POI は、通常の `trackAction` 呼び出しおよび `trackState` 呼び出しの一部としては送信されないので、POI を追跡するには `trackLocation` 呼び出しを使用する必要があります。

* `trackLocation` を必要に応じて呼び出し、ロケーションと POI を追跡してください。

   アプリが開始するときと、アプリケーションの要件で必要になったときに、`trackLocation` を呼び出すことをお勧めします。

* POI が設定されるのは、アプリの設定ファイル内に定義された後のみです。

   以前送信したこれまでの `trackLocation` 呼び出しに対し、POI は適用されません。
* `trackLocation` 呼び出しでは、`trackAction` 呼び出しと同様の追加コンテキストデータの送信がサポートされます。

* 2 つの POI の直径が重複する場合、現在の位置を含む最初の POI が使用されます。

   POI が重複している場合は、粒度の大きい順に POI のリストを並べ替えて、粒度の最も大きい POI がレポートされるようにする必要があります。

