---
description: AdobeSDKを使用して個人情報(PII)を収集し、サードパーティのエンドポイントに送信できます。
seo-description: AdobeSDKを使用して個人情報(PII)を収集し、サードパーティのエンドポイントに送信できます。
seo-title: PII ポストバック
title: PII ポストバック
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 47%

---


# PII ポストバック {#pii-postbacks}

AdobeSDKを使用して個人情報(PII)を収集し、サードパーティのエンドポイントに送信できます。

AdobeSDKを使用してPIIを収集する場合は、PIIトラック呼び出しを送信する必要があります。 この呼び出しを使用すると、PIIデータの収集が有効になりますが、SDKはAdobeエンドポイントにデータを自動的に送信しません。 PII タイプのポストバックは、適切なエンドポイントで設定する必要があります。

>[!TIP]
>
>PII ポストバックタイプを使用するには、HTTPS をサポートするエンドポイントが必要です。

## PII ポストバックの追跡 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

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

