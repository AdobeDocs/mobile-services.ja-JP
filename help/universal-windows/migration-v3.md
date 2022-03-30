---
description: この節では、以前の Windows モバイル SDK の 3.x バージョンから、Experience Cloudソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。
solution: Experience Cloud Services,Analytics
title: 4.x への移行
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# 4.x SDK への移行{#migrate-to-x}

この節では、Windows Mobile SDK の 3.x バージョンからExperience Cloudソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。

バージョン 4.x に移行すると、すべての機能に静的メソッドでアクセスできるようになります。 独自のオブジェクトを追跡する必要がなくなりました。

以降の節では、バージョン 3.x からバージョン 4.x への移行手順について説明します。

## 使用されないプロパティの削除 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新しい `ADBMobileConfig.json` ファイルがダウンロードに含まれています。 このファイルには、アプリケーション固有のグローバル設定が含まれています。以前のバージョンで使用されていた設定変数のほとんどが置き換えられています。

`ADBMobileConfig.json` ファイルの例を次に示します。

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

次の表に、設定ファイルに移動する必要がある設定変数を示します。最初の列の変数に設定されている値を 2 番目の列の変数に移動し、コードから古い設定変数を削除します。

### 3.x からの移行

次の表に、3.x SDK の変数と 4.x SDK の新しい名前の一覧を示します。

| 設定変数/方法 | 変数 `ADBMobileConfig.json` ファイル。 |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | 削除（使用終了） |
| linkTrackVars | 削除（使用終了） |
| linkTrackEvents | 削除（使用終了） |

## トラッキングコールとトラッキング変数の更新 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Web に焦点を当てた `Track` および `TrackLink` 呼び出しの場合、バージョン 4 の SDK では、モバイル環境で少し意味を持つ次の 2 つのメソッドを使用します。

* `TrackState` 状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。 これらの状態は Web サイト上のページによく似ており、`trackState` コールにより、ページビュー数が増分されます。

* `TrackAction` アクションとは、アプリ内で測定に価する重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。 これらの呼び出しは、ページビュー数を増分しません。

この `contextData` 両方のメソッド用のパラメーターには、コンテキストデータとして送信される名前と値のペアが含まれます。

### event、prop、eVar

もし [SDK メソッド](/help/universal-windows/c-configuration/methods.md)イベント、eVar、prop、heir、リストを設定する場所について疑問が生じる場合があります。 バージョン 4 では、これらのタイプの変数を直接アプリに割り当てることができなくなりました。 代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数へとマッピングします。

処理ルールには次の利点があります。

* アプリストアにアップデートを送信しなくてもデータマッピングを変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信しても、影響はほとんどありません。これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

詳しくは、 *処理ルール* セクション [Analytics の概要](/help/universal-windows/analytics/analytics.md).

変数に直接代入していた値は、代わりにコンテキストデータに追加する必要があります。 これは、が `SetProp`, `SetEvar`、および永続コンテキストデータへの割り当てをすべて削除し、値をコンテキストデータに追加する必要があります。

### AppSection／server、GeoZip、トランザクション ID、Campaign、その他の標準的な変数

上記の変数など、測定オブジェクトに設定していたその他のデータは、代わりにコンテキストデータに追加する必要があります。 つまり、 `TrackState` または `TrackAction` 呼び出しは、 `data` パラメーター。

**トラッキングコールの置き換え**

コード全体で、次のメソッドをの呼び出しで置き換えます。 `trackState` または `trackAction`:

**3.x からの移行：**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* 追跡 (TrackAction)
* TrackLinkURL (TrackAction)

## カスタム ID サービス {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を `setUserIdentifier` の呼び出しで置き換えます。

## オフライントラッキング {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

オフライントラッキングは `ADBMobileConfig.json` ファイル。その他のすべてのオフライン設定は自動的におこなわれます。

コード全体で、次のメソッドの呼び出しを削除します。

**3.x からの移行：**

* SetOnline
* SetOffline

## products 変数 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 変数は処理ルールでは使用できないので、以下の構文を使用して `products` を設定することができます。

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

の値 `"&&products"` ( この例では、値は `";Cool Shoe`&quot;) は、追跡するイベントのタイプを表す製品文字列構文に従う必要があります。
