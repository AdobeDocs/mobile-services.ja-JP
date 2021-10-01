---
description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。
title: 保存されている ID の取得
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 67%

---

# 保存されている ID の取得{#retrieving-stored-identifiers}

この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。

GDPR の詳細については、「[GDPR とお客様のビジネス ](https://www.adobe.com/jp/privacy/general-data-protection-regulation.html)」を参照してください。

>[!IMPORTANT]
>
>この `getAllIdentifiersAsync` メソッドは、Experience Cloud SDK に保存されている ID を取得します。このメソッドは、**の前に** 呼び出す必要があります。

Experience CloudSDK ID は（該当する場合）ローカルに保存され、JSON 文字列で返されます。この文字列には次の情報が含まれている可能性があります。

* 会社コンテキスト - IMS 組織 ID
* ユーザー ID
* Experience Cloud ID（MID）、旧称 Experience Cloud ID
* 統合コード（ADID、プッシュ ID）
* データソース ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID、関連する RSID）
* Target の従来の ID(TNTID、TNT3rdpartyID)
* Audience Manager ID（UUID）

iOS の `ADBMobile getAllIdentifiersAsync` メソッドの例を次に示します。

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
