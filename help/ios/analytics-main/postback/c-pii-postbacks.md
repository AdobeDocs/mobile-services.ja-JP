---
description: Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。
seo-description: Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。
seo-title: PII ポストバック
title: PII ポストバック
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII ポストバック {#pii-postbacks}

Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。

Adobe SDK を使用して PII を収集する場合は、追跡 PII 呼び出しを送信する必要があります。この呼び出しを使用すると PII データの収集が可能になりますが、SDK はアドビのエンドポイントにデータを自動的に送信しません。PII タイプのポストバックは、適切なエンドポイントで設定する必要があります。

>[!TIP]
>
>PII ポストバックタイプを使用するには、HTTPS をサポートするエンドポイントが必要です。

## PII ポストバックの追跡 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. PII をキャプチャする準備ができたら、`trackPII` を呼び出して、このアクション、イベントまたはビューのヒットを送信します。

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

