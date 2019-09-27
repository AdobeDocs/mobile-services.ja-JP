---
description: ここでは、以前の Windows Mobile SDK の 3.x バージョンから Experience Cloud ソリューション用 Windows 8.1 ユニバーサルアプリストア 4.x SDK に移行する方法について説明します。
seo-description: ここでは、以前の Windows Mobile SDK の 3.x バージョンから Experience Cloud ソリューション用 Windows 8.1 ユニバーサルアプリストア 4.x SDK に移行する方法について説明します。
seo-title: Migrate to the 4.x SDKs
solution: Marketing Cloud,Analytics
title: Migrate to the 4.x SDKs
topic: 開発者と導入
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# 4.x SDKへの移行 {#migrate-to-the-x-sdks}

ここでは、以前の Windows Mobile SDK の 3.x バージョンから Experience Cloud ソリューション用 Windows 8.1 ユニバーサルアプリストア 4.x SDK に移行する方法について説明します。

バージョン 4.x に移行すると静的メソッドを使用してすべての機能にアクセスできるようになるので、独自のオブジェクトを追跡する必要がなくなります。

以降の節では、バージョン 3.x からバージョン 4.x への移行について説明します。

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

ダウンロードファイルには新しい `ADBMobileConfig.json` ファイルが含まれています。このファイルには、アプリケーション固有のグローバル設定が含まれ、以前のバージョンで使用されていた設定変数のほとんどが置き換えられます。 `ADBMobileConfig.json` ファイルの例を次に示します。

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

## 3.xからの移行

| 設定変数／メソッド | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | 削除します。使用されなくなりました。 |
| linkTrackVars | 削除します。使用されなくなりました。 |
| linkTrackEvents | 削除します。使用されなくなりました。 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

バージョン 4 の SDK では、Web に焦点を当てた `Track` 呼び出しと `TrackLink` 呼び出しを使用する代わりに、モバイルに焦点を当てた次の 2 つのメソッドを使用します。

* `TrackState`状態とは、アプリで使用可能なビューのことで、「home dashboard」、「app settings」、「cart」などがあります。これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

* `TrackAction`アクションとは、アプリ内で測定対象となる重要な操作のことで、「logons」、「banner taps」、「feed subscriptions」などの指標があります。これらの呼び出しは、ページビュー数を増分しません。

これらの両方のメソッドにおいて、`contextData` パラメーターには、コンテキストデータとして送信される名前と値のペアが含まれます。

## event、prop、eVar

[SDKのメソッドを見た場合](/help/windows-appstore/c-configuration/methods.md)、イベント、eVar、prop、相続人、リストを設定する場所が不思議になることがあります。 バージョン 4 では、これらの種類の変数をアプリケーション内で直接割り当てられなくなっています。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

変数に直接代入していた値をコンテキストデータに追加する必要があります。This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection／Server、GeoZip、トランザクション ID、Campaign、その他の標準的な変数**

上記の変数を含め、測定オブジェクトに設定していたデータはコンテキストデータに追加する必要があります。

これを簡単におこなえるように、`TrackState` または `TrackAction` 呼び出しで送信されるデータは `data` パラメーターのペイロードのみになっています。

### トラッキングコールの置き換え

コード全体で、次のメソッドを `trackState` または `trackAction` の呼び出しで置き換えます。

### 3.xからの移行

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

ファイル内でオフライン追跡が有効になっ `ADBMobileConfig.json` ています。 その他すべてのオフライン設定は自動的に行われます。

コード全体で次のメソッドの呼び出しを削除します。

### 3.xからの移行

* `SetOnline`
* `SetOffline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 変数は処理ルールでは使用できないので、以下の構文を使用して `products`products を設定することができます。

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In this example, the value of `"&&products"` is `";Cool Shoe`" and should follow the products string syntax for the type of event that you are tracking.