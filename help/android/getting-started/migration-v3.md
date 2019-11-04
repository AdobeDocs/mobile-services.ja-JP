---
description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
seo-title: Android 4.x ライブラリへの移行
solution: Experience Cloud,Analytics
title: Android 4.x ライブラリへの移行
topic: 開発者と導入
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: ht
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Android 4.x ライブラリへの移行 {#migrating-to-the-android-x-library}

この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。

>[!IMPORTANT]
>
>SDK では、個別ユーザー数の計算に必要なデータ、ライフサイクル指標、SDK の中心機能に関連するその他のデータを保存するために、`SharedPreferences` が使用されます。SDK で想定されている `SharedPreferences` の値を変更または削除すると予期しない動作が発生し、データの不整合が生じる可能性があります。

バージョン 4.x のライブラリでは、パブリックメソッドが 1 つのヘッダーに統合されています。また、クラスレベルのメソッドからすべての機能にアクセスできるようになり、ポインター、インスタンスまたはシングルトンを追跡する必要がなくなりました。

## event、prop、eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

バージョン 4 では、アプリで event、eVar、prop、heir、リストなどの変数を割り当てることができなくなりました。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

>[!TIP]
>
>変数に直接代入していた値を `data` HashMap に追加する必要があります。

## 使用されないプロパティの削除 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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

## 設定ファイルの移動とバージョン 4 への移行 {#section_0B844235E0B04DD4B36976A73DB28FB5}

次の表に、設定ファイルに移動する必要がある設定変数を示します。

### 設定ファイルの移動

1. 先頭列の変数に設定されている値を 2 番目の列の変数に移動します。
1. コードから古い設定変数を削除します。

### バージョン 3.x からの移行

バージョン 3.x から 4 に移行するには、設定変数／メソッド値を `ADBMobileConfig.json` 変数に移します。

| 設定変数またはメソッド | `ADBMobileConfig.json` ファイル内の変数 |
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

バージョン 2.x からバージョン 4 に移行するには、最初の列の値を、2 列目の変数に移します。

| 設定変数 | `ADBMobileConfig.json` ファイル内の変数 |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server"、`"https://"` プレフィックスを削除します。プロトコルプレフィックスは、"ssl" 設定に基づいて自動的に追加されます。 |
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
| useBestPractices  チャーン測定（getChurnInstance）へのすべての呼び出し | ライフサイクル指標による削除、置き換え |

## トラッキングコールとトラッキング変数の更新 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

バージョン 4 の SDK では、Web に焦点を当てた `track` 呼び出しと `trackLink` 呼び出しを使用する代わりに、次のメソッドを使用します。

* `trackState`：アプリ内で使用可能なビューのことで、`cart`、`home dashboard`、`app settings` などがあります。

   これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

* `trackAction`：アプリ内で発生し、測定の対象となる `feed subscriptions`、`logons`、`banner taps` などのアクションを追跡します。

この両方のメソッドにある `contextData` パラメーターは、コンテキストデータとして送信される名前と値のペアを含む `HashMap<String, Object>` です。

## event、prop、eVar 

バージョン 4 では、event、eVar、prop、継承、リストなどの変数をアプリ内で直接割り当てることができなくなりました。SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップするようになりました。

処理ルールには、次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。

   これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。詳しくは、[処理ルールとコンテキストデータ](/help/android/getting-started/proc-rules.md)を参照してください。

変数に直接代入していた値を `data` HashMap に追加する必要があります。つまり、`setEvar` や `setProp` の呼び出し、永続コンテキストデータへの代入を削除し、値を `data` パラメーターに追加する必要があります。

## AppSection／server、GeoZip、トランザクション ID、Campaign、その他の標準的な変数

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

## カスタム訪問者 ID {#section_2CF930C13BA64F04959846E578B608F3}

`visitorID` 変数を `setUserIdentifier` の呼び出しで置き換えます。

## オフライン追跡 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

オフライン追跡は `ADBMobileConfig.json` で有効に設定されます。他のすべてのオフライン設定は自動的におこなわれます。

以下のメソッドに対する呼び出しを削除します。

**バージョン 3.x**

* `setOnline`
* `setOffline`

**バージョン 2.x**

* `forceOffline`
* `forceOnline`

## products 変数{#section_AFBA36F3718C44D29AF81B9E1056A1B4}

products 変数について詳しくは、「[product 変数](/help/android/analytics-main/products/products.md)」を参照してください。

