---
description: この節では、以前の Windows Mobile SDK のバージョン 3.x から、Experience Cloudソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。
solution: Experience Cloud,Analytics
title: 4.x への移行
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# 4.x SDK への移行{#migrate-to-x}

この節では、Windows Mobile SDK の 3.x バージョンから、Experience Cloudソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。

バージョン 4.x に移行すると、すべての機能に静的メソッドを通じてアクセスできるようになります。 独自のオブジェクトを追跡する必要はなくなりました。

以降の節では、バージョン 3.x からバージョン 4.x への移行手順を説明します。

## 使用されないプロパティの削除 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新しい `ADBMobileConfig.json` ファイルがダウンロードに含まれているのに気付いたかもしれません。 このファイルには、アプリケーション固有のグローバル設定が含まれ、以前のバージョンで使用されていた設定変数のほとんどが置き換えられます。

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

次の表に、設定ファイルに移動する必要がある設定変数を示します。最初の列の変数に設定されている値を 2 番目の列の変数に移動し、古い設定変数をコードから削除します。

### 3.x からの移行

次の表に、3.x SDK の変数と 4.x SDK の新しい名前のリストを示します。

| 設定変数/方法 | `ADBMobileConfig.json` ファイル内の変数。 |
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

バージョン 4 の SDK では、Web に焦点を当てた `Track` 呼び出しと `TrackLink` 呼び出しを使用する代わりに、2 つのメソッドを使用してモバイル環境での理解を深めます。

* `TrackState` 状態とは、「home dashboard」、「app settings」、「cart」など、アプリで使用可能なビューです。これらの状態は Web サイト上のページによく似ており、`trackState` コールにより、ページビュー数が増分されます。

* `TrackAction` アクションとは、アプリ内で測定に価する重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。これらの呼び出しでは、ページビュー数は増分されません。

どちらのメソッドも `contextData` パラメーターには、コンテキストデータとして送信される名前と値のペアが含まれます。

### event、prop、eVar

[SDK メソッド ](/help/universal-windows/c-configuration/methods.md) を見てみると、イベント、eVar、prop、heir、リストを設定する場所が分かるかもしれません。 バージョン 4 では、これらのタイプの変数を直接アプリに割り当てることができなくなりました。 代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数へとマッピングします。

処理ルールには次の利点があります。

* アプリストアにアップデートを送信しなくてもデータマッピングを変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信しても、影響はほとんどありません。これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

詳しくは、[Analytics の概要 ](/help/universal-windows/analytics/analytics.md) の *処理ルール* の節を参照してください。

変数に直接割り当てていた値は、代わりにコンテキストデータに追加する必要があります。 つまり、 `SetProp` と `SetEvar` の呼び出しと、永続コンテキストデータへの割り当てをすべて削除し、値をコンテキストデータに追加する必要があります。

### AppSection／server、GeoZip、トランザクション ID、Campaign、その他の標準的な変数

上記の変数を含め、測定オブジェクトに設定していたその他のデータは、代わりにコンテキストデータに追加する必要があります。 つまり、 `TrackState` または `TrackAction` 呼び出しで送信されるデータは、 `data` パラメーターのペイロードのみです。

**トラッキングコールの置き換え**

コード全体で、次のメソッドを `trackState` または `trackAction` の呼び出しで置き換えます。

**3.x からの移行：**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* 追跡 (TrackAction)
* TrackLinkURL (TrackAction)

## カスタム ID サービス {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を `setUserIdentifier` の呼び出しで置き換えます。

## オフライントラッキング {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

オフライン追跡は `ADBMobileConfig.json` ファイルで有効になっています。その他のすべてのオフライン設定は自動的におこなわれます。

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

`"&&products"` の値（この例では値は `";Cool Shoe`&quot;）は、追跡するイベントのタイプの製品文字列構文に従う必要があります。
