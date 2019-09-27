---
description: この情報は、ポストバックの機能とそのしくみを理解するのに役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、ポストバックの機能とそのしくみを理解するのに役立ちます。
seo-title: ポストバックの例
solution: Marketing Cloud,Analytics
title: ポストバックの例
topic: 開発者と導入
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

この情報を使用して、ポストバックとは何か、およびポストバックの仕組みを理解するのに役立ちます。

>[!CAUTION]
>
>この例は、情報提供のみを目的としています。 `ADBMobileConfig.json` ファイルは、Adobe Mobile UI で設定する必要があります。手動で変更しないでください。リモートメッセージの設定が有効になっている場合、手動で編集した設定ファイルは危険を招く可能性があります。

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. この URL では、すべてのテンプレート変数が、ヒットから取得した値に置き換えられます。ユーザーの以前のセッションの長さが132秒で、そのユーザーがAndroid SDKバージョン4.6.0を使用している場合、結果のURLは次のようになります。

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
