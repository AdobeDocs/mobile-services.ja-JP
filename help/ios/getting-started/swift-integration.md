---
description: iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。
solution: Experience Cloud Services,Analytics
title: Swift 統合
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Swift 統合 {#swift-integration}

iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。

詳しくは、「[Language Interoperability（言語の相互互換性）](https://developer.apple.com/documentation/swift#2984801.html)」を参照してください。

例えば、ドキュメントで説明されているブリッジヘッダー方式を使用すると、Adobe Mobile iOS SDK ヘッダーファイルを読み込むことができます。

```
#import "ADBMobile.h"
```

Swift ファイル内の SDK からメソッドにアクセスするには、次の形式を使用します。

```
ADBMobile.{methodname}
```
