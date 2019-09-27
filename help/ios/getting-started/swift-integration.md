---
description: iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。
seo-description: iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。
seo-title: Swift 統合
solution: Marketing Cloud,Analytics
title: Swift 統合
topic: 開発者と導入
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。

詳しくは、「言語の相互運用性」を [参照してください](https://developer.apple.com/documentation/swift#2984801.html)。

例えば、ドキュメントで説明したように、ブリッジヘッダーメソッドを使用して、Adobe Mobile iOS SDK ヘッダーファイルをインポートできます。

```
#import “ADBMobile.h”
```

Swift ファイル内で SDK のメソッドにアクセスするには、以下の形式を使用してください。

```
ADBMobile.{methodname}
```

