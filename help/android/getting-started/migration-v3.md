---
description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
seo-title: Android 4.x ライブラリへの移行
solution: Marketing Cloud,Analytics
title: Android 4.x ライブラリへの移行
topic: 開発者と導入
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  If you modify or remove the values in `SharedPreferences` that are expected by the SDK, unexpected behavior might result in the form of data inconsistencies.

バージョン 4.x のライブラリでは、パブリックメソッドが 1 つのヘッダーに統合されています。また、クラスレベルのメソッドからすべての機能にアクセスできるようになり、ポインター、インスタンスまたはシングルトンを追跡する必要がなくなりました。

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

バージョン 4 では、アプリで event、eVar、prop、heir、リストなどの変数を割り当てることができなくなりました。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

次の表に、設定ファイルに移動する必要がある設定変数を示します。

### 設定ファイルの移動

1. 先頭列の変数に設定されている値を 2 番目の列の変数に移動します。
1. コードから古い設定変数を削除します。

### バージョン 3.x からの移行

To migrate from version 3.x to 4, move the configuration variable/method value to the  variable.`ADBMobileConfig.json`

| 設定変数または方法 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 削除します。使用されなくなりました。 |
| linkTrackEvents | 削除します。使用されなくなりました。 |

### バージョン 2.x からの移行

バージョン2.xからバージョン4に移行するには、最初の列の値を2番目の列の変数に移動します。

| 設定変数 | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the  prefix. `"https://"`プロトコルプレフィックスは、"ssl" 設定に基づいて自動的に追加されます。 |
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
| useBestPracticesチャーン測定（getChurnInstance）へのすべての呼び出し | Remove, replaced by  Lifecycle Metrics. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

バージョン 4 の SDK では、Web に焦点を当てた `track` 呼び出しと `trackLink` 呼び出しを使用する代わりに、次のメソッドを使用します。

* `trackState`, which are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on.

   これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

* `trackAction` アプリで発生 `logons`し、測 `banner taps`定 `feed subscriptions`する、、、などのアクションを設定します。

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## イベント、propおよびeVar

バージョン 4 では、event、eVar、prop、継承、リストなどの変数をアプリ内で直接割り当てることができなくなりました。SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップするようになりました。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。詳しくは、[処理ルールとコンテキストデータ](/help/android/getting-started/proc-rules.md)を参照してください。

変数に直接代入していた値を `data` HashMap に追加する必要があります。This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server, GeoZip, transaction ID, Campaign, and other standard variables

上記の変数を含め、測定オブジェクトに設定していたデータは `data` HashMap に追加する必要があります。`trackState` または `trackAction` 呼び出しで送信されるデータは、`data` パラメーターのペイロードのみです。

### トラッキングコールの置き換え

次のメソッドを `trackState` または `trackAction` の呼び出しで置き換えます。

* **バージョン 3.x からの移行**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **バージョン 2.x からの移行**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

以下のメソッドに対する呼び出しを削除します。

**バージョン 3.x**

* `setOnline`
* `setOffline`

**バージョン 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

