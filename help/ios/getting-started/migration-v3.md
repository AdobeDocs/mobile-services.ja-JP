---
description: iOS ライブラリのバージョン 3.x または 2.x からバージョン 4.x への移行に役立つ情報です。
seo-description: iOS ライブラリのバージョン 3.x または 2.x からバージョン 4.x への移行に役立つ情報です。
seo-title: 4. x iOSライブラリへの移行
solution: Marketing Cloud、Analytics
title: 4. x iOSライブラリへの移行
topic: 開発者と導入
uuid: 5668972b- f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

iOS ライブラリのバージョン 3.x または 2.x からバージョン 4.x への移行に役立つ情報です。

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  If you modify or remove the values in `NSUserDefaults` that are expected by the SDK, unexpected behavior might result in the form of data inconsistencies.

iOS SDKライブラリのバージョン4. xでは、パブリックメソッドは1つのヘッダーに統合されています。また、機能はクラスレベルメソッドからアクセスできるようになったため、ポインター、インスタンス、またはシングルトンを追跡する必要はありません。

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

バージョン 4 では、event、eVar、prop、継承、リストなどの変数をアプリ内で直接割り当てることができなくなりました。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新しい `ADBMobileConfig.json` ファイルには、アプリケーション固有のグローバル設定が含まれています。以前のバージョンで使用されていた設定変数のほとんどは置き換えられています。`ADBMobileConfig.json` ファイルの例を次に示します。

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
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


### 設定ファイルの移動

設定ファイルを移動するには：

1. 先頭列の変数に設定されている値を 2 番目の列の変数に移動します。
1. コードから古い設定変数を削除します。

### 移行情報

次の表に、設定ファイルに移動する必要がある設定変数を示します。

#### バージョン 3.x からの移行

先頭列の値を 2 番目の列の変数に移動します。

| 設定変数 | `ADBMobileConfig.json` ファイル内の変数 |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| offlineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 削除します。使用されなくなりました。 |
| linkTrackEvents | 削除します。使用されなくなりました。 |


#### バージョン 2.x からの移行

先頭列の値を 2 番目の列の変数に移動します。

| 設定変数 | `ADBMobileConfig.json` ファイル内の変数 |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server"の場合は、プレフィックスを `"https://"` 削除します。プロトコルプレフィックスは、"ssl" 設定に基づいて自動的に追加されます。 |
| trackingServerSecure | 削除します。安全な接続をおこなうには、"server" を定義し、"ssl" を有効にします。 |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 削除します。使用されなくなりました。 |
| linkTrackEvents | 削除します。使用されなくなりました。 |
| timestamp | 削除します。設定できなくなりました。 |
| dc | 削除します。使用されなくなりました。 |
| userAgent | 削除します。設定できなくなりました。 |
| dynamicVariablePrefix | 削除します。使用されなくなりました。 |
| visitorNamespace | 削除します。使用されなくなりました。 |
| usePlugins | 削除します。使用されなくなりました。 |
| useBestPracticesチャーン測定（getChurnInstance）へのすべての呼び出し | 削除し、ライフサイクル指標に置き換えます。詳しくは、[ライフサイクル指標](//help/ios/metrics.md)を参照してください。 |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

バージョン 4 の SDK では、Web に焦点を当てた `track` 呼び出しと `trackLink` 呼び出しを使用する代わりに、次のメソッドを使用します。

* `trackState:data:` 状態は、アプリで使用可能なビュー（など `home dashboard``app settings``cart`）です。

   これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

* `trackAction:data:` アクション（ `logons``banner taps``feed subscriptions`例えば、アプリで発生し、測定したい指標など）を実行します。

どちらのメソッドも `data` パラメーターを使用しますが、これは、コンテキストデータとして送信される名前と値のペアを含む `NSDictionary` です。

### イベント、prop、eVar

バージョン 4 では、event、eVar、prop、継承、リストなどの変数をアプリ内で直接割り当てることができなくなりました。SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップするようになりました。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマッピングするまではレポートに表示されません。詳しくは、[処理ルールとコンテキストデータ](/help/ios/getting-started/proc-rules.md)を参照してください。

代わりに、変数に直接割り当てた値を `data``NSDictionary`   に追加する必要があります。This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### appSection/Server、geoZip、トランザクションID、キャンペーン、その他の標準変数

上記の変数など、測定オブジェクトに設定していたデータを代わりに `data``NSDictionary`   に追加する必要があります。`trackState` または `trackAction` 呼び出しで送信されるデータは、`data` パラメーターのペイロードのみです。

### トラッキングコールの置換

コードで、次のメソッドを `trackState` または `trackAction` の呼び出しで置き換えます。

#### バージョン 3.x からの移行

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### バージョン 2.x からの移行

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を呼び出しに置き換え `setUserIdentifier:`ます。

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

コード内の次のメソッドの呼び出しを削除します。

### バージョン 3.x

* `setOnline`
* `setOffline`

### バージョン 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

 変数は処理ルールでは使用できないので、以下の構文を使用して `products`products を設定することができます。

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)