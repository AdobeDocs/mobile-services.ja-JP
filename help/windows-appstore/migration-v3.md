---
description: この節では、以前のWindowsモバイルSDK 3.xバージョンからWindows 8.1ユニバーサルアプリストア4.x SDK forExperience Cloudソリューションに移行する方法について説明します。
seo-description: この節では、以前のWindowsモバイルSDK 3.xバージョンからWindows 8.1ユニバーサルアプリストア4.x SDK forExperience Cloudソリューションに移行する方法について説明します。
seo-title: 4.x SDKへの移行
solution: Experience Cloud,Analytics
title: 4.x SDKへの移行
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 24%

---

# 4.x SDKへの移行{#migrate-to-the-x-sdks}

この節では、以前のWindowsモバイルSDK 3.xバージョンからWindows 8.1ユニバーサルアプリストア4.x SDK forExperience Cloudソリューションに移行する方法について説明します。

バージョン4.xに移行すると、すべての機能に静的メソッドでアクセスできるようになり、独自のオブジェクトを追跡しなくなります。

次の節では、バージョン3.xからバージョン4.xへの移行手順を説明します。

## 使用されないプロパティの削除 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新しい`ADBMobileConfig.json`ファイルがダウンロードに含まれているのに気づいたかもしれません。 このファイルには、アプリケーション固有のグローバル設定が含まれ、以前のバージョンで使用されていた設定変数のほとんどが置き換えられます。 `ADBMobileConfig.json` ファイルの例を次に示します。

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

次の表に、設定ファイルに移動する必要がある設定変数を示します。1列目の変数に設定された値を2列目の変数に移動し、古い設定変数をコードから削除します。

## 3.xからの移行

| 設定変数/方法 | `ADBMobileConfig.json`ファイル内の変数。 |
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

バージョン4 SDKは、Web中心の`Track`呼び出しと`TrackLink`呼び出しを使用する代わりに、モバイル業界で少し意味のある2つのメソッドを使用します。

* `TrackState` 状態は、「ホームダッシュボード」、「アプリ設定」、「カート」など、アプリで使用できる表示です。これらの状態は Web サイト上のページによく似ており、`trackState` コールにより、ページビュー数が増分されます。

* `TrackAction` アクションとは、「ログオン」、「バナーのタップ」、「フィード購読」など、測定対象のアプリで発生する操作です。これらの呼び出しでは、ページ表示は増えません。

これらの両方のメソッドの`contextData`パラメーターには、コンテキストデータとして送信される名前と値のペアが含まれています。

## イベント、Prop、eVar

[SDKメソッド](/help/windows-appstore/c-configuration/methods.md)を参照した場合、イベント、eVar、prop、ヒーラー、リストの設定場所を考えているでしょう。 バージョン4では、これらのタイプの変数を直接アプリで割り当てることはできなくなりました。 代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数へとマッピングします。

処理ルールには、次のようないくつかの利点があります。

* アプリストアにアップデートを送信しなくてもデータマッピングを変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信しても、影響はほとんどありません。これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

詳しくは、[Analytics](/help/windows-appstore/analytics/analytics.md)の&#x200B;*処理ルール*&#x200B;を参照してください。

変数に直接割り当てた値は、代わりにコンテキストデータに追加する必要があります。 つまり、`SetProp`、`SetEvar`への呼び出し、および永続的なコンテキストデータへの割り当ては、すべて削除され、コンテキストデータに追加された値が追加されます。

**AppSection/Server、GeoZip、トランザクションID、キャンペーン、その他の標準変数**

測定オブジェクトに設定したその他のデータ（上記の変数を含む）は、コンテキストデータに追加する必要があります。

単純に言うと、`TrackState`または`TrackAction`呼び出しと共に送信されるデータは、`data`パラメーター内のペイロードのみです。

### トラッキングコールの置き換え

コード全体で、次のメソッドを`trackState`または`trackAction`への呼び出しで置き換えます。

### 3.xからの移行

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## カスタム訪問者 ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を `setUserIdentifier` の呼び出しで置き換えます。

## オフライントラッキング {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

オフライン追跡は`ADBMobileConfig.json`ファイルで有効になっています。その他すべてのオフライン設定は自動的に行われます。

コード全体で、次のメソッドの呼び出しを削除します。

### 3.xからの移行

* `SetOnline`
* `SetOffline`

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

この例では、`"&&products"`の値は`";Cool Shoe`&quot;で、追跡するイベントのタイプの製品文字列構文に従う必要があります。
