---
description: ここでは、Windows モバイル SDK バージョン 3.x から Experience Cloud ソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。
seo-description: ここでは、Windows モバイル SDK バージョン 3.x から Experience Cloud ソリューション用 Universal Windows Platform 4.x SDK に移行する方法について説明します。
seo-title: 4. xに移行
solution: Marketing Cloud、Analytics
title: 4. xに移行
topic: 開発者と導入
uuid: bdd6c5cd-3892-4e99- b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# 4. x SDKへの移行{#migrate-to-x}

ここでは、WindowsモバイルSDKの3. xバージョンからUniversal Windows Platform4. x SDKへの移行方法について説明します。

バージョン4. xへの移行により、静的メソッドですべての機能にアクセスできるようになりました。独自のオブジェクトを追跡する必要はなくなりました。

以降の節では、バージョン 3.x からバージョン 4.x への移行について説明します。

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

ダウンロードファイルには新しい `ADBMobileConfig.json` ファイルが含まれています。このファイルには、アプリケーション固有のグローバル設定が含まれています。以前のバージョンで使用されていた設定変数のほとんどは置き換えられています。

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

### 3. xからの移行

次の表に、3. x SDK内の変数と4. x SDKの新しい名前のリストを示します。

| 設定変数／メソッド | `ADBMobileConfig.json` ファイル内の変数。 |
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

### イベント、prop、eVar

[SDKメソッド](/help/universal-windows/c-configuration/methods.md)を見ている場合は、イベント、eVar、prop、heies、およびリストを設定することをお勧めします。バージョン 4 では、これらの種類の変数をアプリケーション内で直接割り当てられなくなっています。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

詳しくは、Analyticsの概要の *「処理ルール* 」の節 [](/help/universal-windows/analytics/analytics.md)を参照してください。

変数に直接代入していた値をコンテキストデータに追加する必要があります。This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### appSection/Server、geoZip、トランザクションID、キャンペーン、その他の標準変数

上記の変数を含め、測定オブジェクトに設定していたデータはコンテキストデータに追加する必要があります。つまり、また `TrackState``TrackAction` は呼び出しとともに送信される唯一のデータは `data` 、パラメーターのペイロードです。

**トラッキングコールの置換**

コード全体で、次のメソッドを `trackState` または `trackAction` の呼び出しで置き換えます。

**3.x からの移行：**

* TrackAppState（TrackState）
* TrackEvents（TrackAction）
* Track（TrackAction）
* TrackLinkURL（TrackAction）

## カスタム ID サービス {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を呼び出しに置き換え `setUserIdentifier`ます。

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

`ADBMobileConfig.json` ファイル内でオフライン追跡が有効になります。その他すべてのオフライン設定は自動的に実行されます。

コード全体で次のメソッドの呼び出しを削除します。

**3.x からの移行：**

* SetOnline
* SetOffline

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

`"&&products"` （この例では）値の値は、追跡する `";Cool Shoe`イベントのタイプの製品文字列構文に従う必要があります。
