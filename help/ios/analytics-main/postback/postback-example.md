---
description: ポストバック機能の定義およびソースコードのサンプルです。
seo-description: ポストバック機能の定義およびソースコードのサンプルです。
seo-title: ポストバックのサンプル
solution: Marketing Cloud、Analytics
title: ポストバックのサンプル
topic: 開発者と導入
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

ポストバック機能の定義およびソースコードのサンプルです。

>[!CAUTION]
>
>この例は、情報提供のみを目的としています。`ADBMobileConfig.json` ファイルは、Adobe Mobile UI で設定する必要があります。手動で変更しないでください。リモートメッセージの設定が有効になっている場合、手動で編集した設定ファイルは危険を招く可能性があります。

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URLによって、すべてのテンプレート変数がヒットの値に置き換えられます。ユーザーの以前のセッションが132秒で、そのユーザーがiOS SDKバージョン4.6.0にあると仮定した場合、次のURLの例を示します。

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
