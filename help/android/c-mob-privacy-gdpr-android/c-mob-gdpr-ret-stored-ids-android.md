---
description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。
seo-description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。
seo-title: 保存されている ID の取得
title: 保存されている ID の取得
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 76%

---


# 保存されている ID の取得{#retrieving-stored-identifiers}

この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。

>[!IMPORTANT]
>
>SDK に保存されている ID を取得するには `getAllIdentifiersAsync` メソッドを使用します。You must call this method **before** the user opts-out.

SDKのID（該当する場合）は、ローカルに保存され、JSON文字列として返されます。SDKには次の情報が含まれます。

* 会社コンテキスト - IMS 組織 ID
* ユーザー ID
* Experience Cloud ID（MID）、旧称 Experience Cloud ID
* 統合コード（ADID、プッシュID）
* データソース ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID、関連する RSID）
* ターゲットのレガシーID(TNTID、TNT3rdpartyID)
* Audience Manager ID（UUID）

Android の `ADBMobile getAllIdentifiersAsync` メソッドの例を次に示します。

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
