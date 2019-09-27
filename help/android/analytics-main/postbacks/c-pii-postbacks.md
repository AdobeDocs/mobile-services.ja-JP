---
description: Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。
seo-description: Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。
seo-title: PII ポストバック
title: PII ポストバック
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

Adobe SDK を使用して、個人識別情報（PII）を収集し、サードパーティのエンドポイントに送信することができます。

Adobe SDK を使用して PII を収集する場合は、追跡 PII 呼び出しを送信する必要があります。このコールを使用して PII データを収集することはできますが、SDK はそのデータを Adobe エンドポイントに自動的には送信しません。PII タイプのポストバックは、適切なエンドポイントで設定する必要があります。

>[!TIP]
>
>An endpoint that supports HTTPS is required to use the PII postback type.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. [ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、 *Core実装およびライフサイクルのIntelliJ IDEAまたはEclipse ProjectへのSDKと設定ファイルの追加*[を参照してください](/help/android/getting-started/dev-qs.md)。

1. ライブラリをインポートします。

   ```java
   #import "ADBMobile.h"
   ```

1. PII をキャプチャする準備ができたら、`trackPII` を呼び出して、このアクション、イベントまたはビューのヒットを送信します。

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

