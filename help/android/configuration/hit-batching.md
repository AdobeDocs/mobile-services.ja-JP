---
description: ヒットのバッチ処理では、キュー内のヒット数が設定済みの制限を超えるまで、ヒットの送信を抑制できます。
keywords: android;library;mobile;sdk
seo-description: ヒットのバッチ処理では、キュー内のヒット数が設定済みの制限を超えるまで、ヒットの送信を抑制できます。
seo-title: ヒットのバッチ処理
solution: Marketing Cloud、Analytics
title: ヒットのバッチ処理
topic: 開発者と導入
uuid: ada35be3-242b-4b2b- a828-9bf998dd58b5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ヒットのバッチ処理 {#hit-batching}

ヒットのバッチ処理では、キュー内のヒット数が設定済みの制限を超えるまで、ヒットの送信を抑制できます。

>[!IMPORTANT]
>
>ヒットのバッチ処理を使用するに **は** 、オフライン追跡を有効にし、SDKバージョン4.1以降を使用する必要があります

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. このしきい値を超えると、キュー内のすべてのヒットが送信されます。

ヒットのバッチ処理では、次のメソッドが使用されます。

* `Analytics.getQueueSize` は、ヒットのバッチ処理キュー内の現在のヒット数を示す `long` を返します。

* `Analytics.sendQueuedHits` は、現在キューに格納されているヒット数にかかわらず、キュー内のすべてのヒットを強制的に送信します。
* `Analytics.clearQueue` は、キュー内のすべてのヒットを送信せずにクリアします。
