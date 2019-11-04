---
description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。
seo-description: この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。
seo-title: 保存されている ID の取得
title: 保存されている ID の取得
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 保存されている ID の取得{#retrieving-stored-identifiers}

この情報は、GDPR のデータアクセス要求に関連してローカルに保存されている SDK ID を Android アプリから取得する場合に役立ちます。

>[!IMPORTANT]
>
>SDK に保存されている ID を取得するには `getAllIdentifiersAsync` メソッドを使用します。このメソッドは、ユーザーがオプトアウトする&#x200B;**前**&#x200B;に呼び出す必要があります。

（存在する場合）SDK ID はローカルに保存され、JSON 文字列で返されます。この文字列には次の情報が含まれている可能性があります。

* 会社コンテキスト - IMS 組織 ID
* ユーザー ID
* Experience Cloud ID（MID）、旧称 Experience Cloud ID
* 統合コード（ADID、プッシュ ID）
* データソース ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID、関連する RSID）
* ターゲットレガシー ID（TNTID、TNT3rdpartyID）
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
