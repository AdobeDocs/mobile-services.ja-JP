---
description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。
seo-description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。
seo-title: 格納された識別子の取得
title: 格納された識別子の取得
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 69%

---


# 保存されている ID の取得{#retrieving-stored-identifiers}

この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。

GDPRの詳細については、「 [GDPRとYour Business](https://www.adobe.com/jp/privacy/general-data-protection-regulation.html)」を参照してください。

>[!IMPORTANT]
>
>この `getAllIdentifiersAsync` メソッドは、Experience Cloud SDK に保存されている ID を取得します。You must call this method **before** the user opts-out.

Experience CloudSDK IDは（該当する場合に）ローカルに保存され、JSON文字列として返されます。この文字列には、次の情報が含まれます。

* 会社コンテキスト - IMS 組織 ID
* ユーザー ID
* Experience Cloud ID（MID）、旧称 Experience Cloud ID
* 統合コード（ADID、プッシュID）
* データソース ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID、関連する RSID）
* ターゲットのレガシーID(TNTID、TNT3rdpartyID)
* Audience Manager ID（UUID）

iOS の `ADBMobile getAllIdentifiersAsync` メソッドの例を次に示します。

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

