---
description: ビーコン追跡では、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。
keywords: android;library;mobile;sdk
seo-description: ビーコン追跡では、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。
seo-title: ビーコン追跡
solution: Marketing Cloud,Analytics
title: ビーコン追跡
topic: 開発者と導入
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# ビーコン追跡 {#beacon-tracking}

ビーコン追跡では、iBeacon と Bluetooth Low Energy を使用して、マイクロ位置を測定し、ターゲットにすることができます。

`trackBeacon` が呼び出されると、次のビーコンデータが Analytics と Target に送信されます。

* `a.beacon.uuid`  — ビーコンのProximityUUID
* `a.beacon.major` - ビーコンのメジャー番号（ストア番号など）
* `a.beacon.minor` - ビーコンのマイナー番号（ストア内の一意の番号など）
* `a.beacon.prox` - 0 ～ 3 の値でユーザーとビーコンの距離を表します。

以下に、これらの値の意味を示します。

* 0 = unknown
* 1 = immediate
* 2 = near
* 3 = far

このビーコンデータは、モバイルソリューションの変数にキャプチャされます。

## Track beacons {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. ビーコンの位置を収集します。

   ビーコンの製造元に応じて、Bluetooth LE ビーコンをスキャンするのに複数のサードパーティのライブラリを利用できます。
1. ビーコン情報が取得された後、以下の呼び出しを使用して位置を追跡します。

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

1. ユーザーがビーコンの Proximity を離れたら、現在のビーコンをクリアします。

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

ビーコンデータに加えて、各 `trackBeacon` 呼び出しで追加のコンテキストデータを送信することができます。

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

コンテキストデータ値は、Adobe Mobileサービスのカスタム変数にマップする必要があります。

![](assets/map-variable-context-ltv.png)

