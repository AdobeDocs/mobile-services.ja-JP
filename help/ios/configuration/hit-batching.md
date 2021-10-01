---
description: ヒットのバッチ処理を使用すると、オフライン追跡が有効になっているアプリケーションで、ヒットをすぐに送信せず、キュー内のヒット数が指定の制限を超えるまで送信を保留することができます。
solution: Experience Cloud,Analytics
title: ヒットのバッチ処理
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# ヒットのバッチ処理 {#hit-batching}

ヒットのバッチ処理を使用すると、オフライン追跡が有効になっているアプリケーションで、ヒットをすぐに送信せず、キュー内のヒット数が指定の制限を超えるまで送信を保留することができます。

>[!IMPORTANT]
>
>ヒットのバッチ処理には、SDK バージョン 4.1 以降が必要です。

ヒットのバッチ処理を有効にするには、`ADBMobileConfig.json` ファイルを更新して `batchLimit` の値を指定します。

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

0 より大きい数を設定すると、SDK は *`batchLimit`* と等しいヒット数をキューに追加します。このしきい値が渡されると、キュー内のすべてのヒットが送信されます。

ヒットのバッチ処理では、次のメソッドを使用します。

* `trackingGetQueueSize()`：現在ヒットのバッチ処理キュー内にある `NSUInteger` とヒット数を返します。
* `trackingSendQueuedHits()`：現在キューに格納されているヒット数にかかわらず、キュー内のすべてのヒットを強制的に送信します。
* `trackingClearQueue()` は、キュー内のすべてのヒットを送信せずにクリアします。

>[!CAUTION]
>
>ヒットのバッチ処理を使用するには、オフライン追跡を有効にする必要があります。
