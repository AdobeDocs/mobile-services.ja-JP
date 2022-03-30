---
description: ヒットのバッチ処理では、キュー内のヒット数が設定済みの制限を超えるまで、ヒットの送信を抑制できます。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud Services,Analytics
title: ヒットのバッチ処理
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# ヒットのバッチ処理 {#hit-batching}

ヒットのバッチ処理では、キュー内のヒット数が設定済みの制限を超えるまで、ヒットの送信を抑制できます。

>[!IMPORTANT]
>
>ヒットのバッチ処理を使用するには、オフライン追跡を&#x200B;**有効**&#x200B;にし、SDK バージョン 4.1 以降を持っている必要があります。

ヒットのバッチ処理を有効にするには、`ADBMobileConfig.json` ファイルを更新して `batchLimit` の値を指定します。

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

値に 0 より大きい数を設定すると、SDK は *`batchLimit`* の値と等しいヒット数をキューに追加します。このしきい値が渡されると、キュー内のすべてのヒットが送信されます。

ヒットのバッチ処理では、次のメソッドを使用します。

* `Analytics.getQueueSize` は、ヒットのバッチ処理キュー内の現在のヒット数を示す `long` を返します。

* `Analytics.sendQueuedHits` は、現在キューに格納されているヒット数にかかわらず、キュー内のすべてのヒットを強制的に送信します。
* `Analytics.clearQueue` は、キュー内のすべてのヒットを送信せずにクリアします。
