---
description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。
seo-description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。
seo-title: 保存されている ID の取得
title: 保存されている ID の取得
uuid: 4fb2c166-6700-4f8b- b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている Experience Cloud SDK ID を iOS アプリから取得する場合に役立ちます。

GDPR について詳しくは、[GDPR とビジネス](https://www.adobe.com/privacy/general-data-protection-regulation.html)を参照してください。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` このメソッドは、Experience Cloud SDKに格納されているIDを取得します。このメソッドは、ユーザーがオプトアウトする&#x200B;**前**&#x200B;に呼び出す必要があります。

（存在する場合）Experience Cloud SDK ID はローカルに保存され、JSON 文字列で返されます。この文字列には次の情報が含まれている可能性があります。

* 会社コンテキスト - IMS 組織 ID
* ユーザー ID
* Experience Cloud ID（MID）、旧称 Marketing Cloud ID
* 統合コード（ADID、プッシュ ID）
* データソース ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID、関連する RSID）
* ターゲットレガシー ID（TNTID、TNT3rdpartyID）
* Audience Manager ID（UUID）

iOS の `ADBMobile getAllIdentifiersAsync` メソッドの例を次に示します。

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

