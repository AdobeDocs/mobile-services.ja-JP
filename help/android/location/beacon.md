---
description: ビーコントラッキングでは、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。
keywords: android;library;mobile;sdk
seo-description: ビーコントラッキングでは、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。
seo-title: ビーコントラッキング
solution: Experience Cloud,Analytics
title: ビーコントラッキング
topic: Developer and implementation
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '240'
ht-degree: 100%

---


# ビーコントラッキング {#beacon-tracking}

ビーコントラッキングでは、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。

`trackBeacon` が呼び出されると、次のビーコンデータが Analytics と Target に送信されます。

* `a.beacon.uuid` - ビーコンの ProximityUUID
* `a.beacon.major` - ビーコンのメジャー番号（ストア番号など）
* `a.beacon.minor` - ビーコンのマイナー番号（ストア内の一意の番号など）
* `a.beacon.prox` - 0 ～ 3 の値でユーザーとビーコンの距離を表します。

これらの値の意味は次のとおりです：

* 0 = 不明
* 1 = 即時
* 2 = 近い
* 3 = 遠い

このビーコンデータは、モバイルソリューションの変数にキャプチャされます。

## ビーコンの追跡 {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. ビーコンの場所を収集します。

   ビーコンの製造元に応じて、Bluetooth LE ビーコンをスキャンする複数のサードパーティライブラリを使用できます。
1. ビーコン情報を取得したら、次の呼び出しを使用して場所を追跡します。

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. ユーザーがビーコンの付近から離れたら、現在のビーコンをクリアします。

   ```java
   Analytics.clearBeacon();
   ```

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

ビーコンデータに加えて、各 `trackBeacon` 呼び出しで追加のコンテキストデータを送信することができます。

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

コンテキストデータ値は、Adobe Mobile Services でカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-ltv.png)

