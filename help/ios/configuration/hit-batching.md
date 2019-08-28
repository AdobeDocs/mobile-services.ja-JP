---
description: ヒットのバッチ処理を使用すると、オフライン追跡が有効になっているアプリケーションで、ヒットをすぐに送信せず、キュー内のヒット数が指定の制限を超えるまで送信を保留することができます。
seo-description: ヒットのバッチ処理を使用すると、オフライン追跡が有効になっているアプリケーションで、ヒットをすぐに送信せず、キュー内のヒット数が指定の制限を超えるまで送信を保留することができます。
seo-title: ヒットのバッチ処理
solution: Marketing Cloud、Analytics
title: ヒットのバッチ処理
topic: 開発者と導入
uuid: 3dda7372-0695-4cb7- b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# ヒットのバッチ処理 {#hit-batching}

ヒットのバッチ処理を使用すると、オフライン追跡が有効になっているアプリケーションで、ヒットをすぐに送信せず、キュー内のヒット数が指定の制限を超えるまで送信を保留することができます。

>[!IMPORTANT]
>
>ヒットのバッチ処理にはSDKバージョン4.1以降が必要です。

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When set to a number higher than 0, the SDK queues the number of hits equal to *`batchLimit`*. このしきい値を超えると、キュー内のすべてのヒットが送信されます。

ヒットのバッチ処理では、次のメソッドが使用されます。

* `trackingGetQueueSize()` は、現在ヒットバッチキューに含まれているヒット数 `NSUInteger` を返します。
* `trackingSendQueuedHits()` ライブラリが、現在キューに格納されているのに関係なく、キュー内のすべてのヒットを強制的に送信します。
* `trackingClearQueue()` は、キュー内のすべてのヒットを送信せずにクリアします。

>[!CAUTION]
>
>ヒットのバッチ処理を使用するには、オフライン追跡を有効にする必要があります。

