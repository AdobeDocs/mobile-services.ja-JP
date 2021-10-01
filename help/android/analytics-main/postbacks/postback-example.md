---
description: この情報は、ポストバックの機能とそのしくみを理解するのに役立ちます。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: ポストバックの例
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 99%

---

# ポストバックの例 {#postbacks-example}

この情報は、ポストバックの機能とそのしくみを理解するのに役立ちます。

>[!CAUTION]
>
>このサンプルは、参照用としてのみ提供されています。`ADBMobileConfig.json` ファイルは、Adobe Mobile UI で設定する必要があります。手動で変更しないでください。リモートメッセージの設定が有効になっている場合、手動で編集した設定ファイルは危険を招く可能性があります。

## `ADBMobileConfig.json` 定義 {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## コードサンプル {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

状態が `"MainMenu"` なので、このトラッキングコールは上記のポストバックメッセージをトリガーします。この URL では、すべてのテンプレート変数が、ヒットから取得した値に置き換えられます。ユーザーの前のセッションの時間が 132 秒で、そのユーザーが Android SDK バージョン 4.6.0 を使用していたと仮定すると、URL は次のようになります。

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
