---
description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。
seo-title: Android 4.x ライブラリへの移行
solution: Experience Cloud,Analytics
title: Android 4.x ライブラリへの移行
topic: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 59%

---


# Android 4.x ライブラリへの移行 {#migrating-to-the-android-x-library}

この情報は、Android ライブラリのバージョン 3.x または 2.x をバージョン 4.x に移行する場合に役立ちます。

>[!IMPORTANT]
>
>SDK では、個別ユーザー数の計算に必要なデータ、ライフサイクル指標、SDK の中心機能に関連するその他のデータを保存するために、`SharedPreferences` が使用されます。SDK で想定されている `SharedPreferences` の値を変更または削除すると予期しない動作が発生し、データの不整合が生じる可能性があります。

バージョン4.xライブラリでは、パブリックメソッドは1つのヘッダーに統合されています。 また、すべての機能はクラスレベルメソッドを通じてアクセスできるようになったので、ポインタ、インスタンス、シングルトンを追跡する必要はありません。

## event、prop、eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

バージョン4では、アプリ内のイベント、eVar、prop、相続人、リストなどの変数を割り当てることができなくなりました。 代わりに、SDKは、コンテキストデータと処理ルールを使用して、レポート用にアプリデータをAnalytics変数にマッピングします。

処理ルールには次の利点があります。

* データマッピングは、更新をApp Storeに送信しなくても変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信する場合、影響はほとんどありません。

   これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

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

1. 1列目の変数に設定されている値を2列目の変数に移動します。
1. コードから古い設定変数を削除します。

### バージョン 3.x からの移行

バージョン 3.x から 4 に移行するには、設定変数／メソッド値を `ADBMobileConfig.json` 変数に移します。

| 設定変数またはメソッド | `ADBMobileConfig.json` ファイル内の変数 |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 削除（使用終了） |
| linkTrackEvents | 削除（使用終了） |

### バージョン 2.x からの移行

バージョン 2.x からバージョン 4 に移行するには、最初の列の値を、2 列目の変数に移します。

| 設定変数 | `ADBMobileConfig.json` ファイル内の変数 |
| --- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, remove the `"https://"` prefix. 「ssl」設定に基づいて、プロトコルプレフィックスが自動的に追加されます。 |
| trackingServerSecure | 削除. 安全な接続の場合は、「server」を定義し、「ssl」を有効にします。 |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 削除（使用終了） |
| linkTrackEvents | 削除（使用終了） |
| timestamp | 削除（設定不可） |
| dc | 削除（使用終了） |
| userAgent | 削除（設定不可） |
| dynamicVariablePrefix | 削除（使用終了） |
| visitorNamespace | 削除（使用終了） |
| usePlugins | 削除（使用終了） |
| useBestPracticesは、測定をチャーン化する(getChurnInstance)ためのすべての呼び出しを行います。 | ライフサイクル指標による削除、置き換え |

## トラッキングコールとトラッキング変数の更新 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

バージョン 4 の SDK では、Web に焦点を当てた `track` 呼び出しと `trackLink` 呼び出しを使用する代わりに、次のメソッドを使用します。

* `trackState`：アプリ内で使用可能なビューのことで、`cart`、`home dashboard`、`app settings` などがあります。

   これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

* `trackAction`：アプリ内で発生し、測定の対象となる `feed subscriptions`、`logons`、`banner taps` などのアクションを追跡します。

この両方のメソッドにある `contextData` パラメーターは、コンテキストデータとして送信される名前と値のペアを含む `HashMap<String, Object>` です。

## event、prop、eVar 

バージョン4では、イベント、eVar、prop、相続人、リストなどの変数を直接アプリに割り当てることができなくなりました。 SDKは、コンテキストデータと処理ルールを使用して、レポートのためにアプリデータをAnalytics変数にマップするようになりました。

処理ルールには次の利点があります。

* データマッピングは、更新をApp Storeに送信しなくても変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信する場合、影響はほとんどありません。

   これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。 詳しくは、 [処理ルールとコンテキストデータを参照してください](/help/android/getting-started/proc-rules.md)。

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

次のメソッドへの呼び出しを削除します。

**バージョン 3.x**

* `setOnline`
* `setOffline`

**バージョン 2.x**

* `forceOffline`
* `forceOnline`

## products 変数{#section_AFBA36F3718C44D29AF81B9E1056A1B4}

products 変数について詳しくは、「[product 変数](/help/android/analytics-main/products/products.md)」を参照してください。

