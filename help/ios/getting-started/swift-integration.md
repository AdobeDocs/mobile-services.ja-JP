---
description: iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。
seo-description: iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。
seo-title: Swift 統合
solution: Experience Cloud,Analytics
title: Swift 統合
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 71%

---


# Swift 統合 {#swift-integration}

iOS 開発者ライブラリのミックス＆マッチ機能を使用して、iOS Adobe Mobile SDK を Swift プロジェクトにシームレスに統合できます。

詳しくは、「[Language Interoperability（言語の相互互換性）](https://developer.apple.com/documentation/swift#2984801.html)」を参照してください。

例えば、ドキュメントで説明されているブリッジヘッダー方式を使用すると、AdobeモバイルiOS SDKヘッダーファイルを読み込むことができます。

```
#import “ADBMobile.h”
```

Swiftファイル内のSDKからメソッドにアクセスするには、次の形式を使用します。

```
ADBMobile.{methodname}
```

