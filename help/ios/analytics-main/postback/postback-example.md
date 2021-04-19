---
description: ポストバック機能の定義およびソースコードのサンプルです。
seo-description: ポストバック機能の定義およびソースコードのサンプルです。
seo-title: ポストバックのサンプル
solution: Experience Cloud,Analytics
title: ポストバックのサンプル
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 100%

---

# ポストバックのサンプル {#postback-example}

ポストバック機能の定義およびソースコードのサンプルです。

>[!CAUTION]
>
>このサンプルは、参照用としてのみ提供されています。`ADBMobileConfig.json` ファイルは、Adobe Mobile UI で設定する必要があります。手動で変更しないでください。リモートメッセージの設定が有効になっている場合、手動で編集した設定ファイルは危険を招く可能性があります。

## ADBMobileConfig.json の定義 {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## コードサンプル {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

状態が `“MainMenu”` なので、このトラッキングコールは上記のポストバックメッセージをトリガーします。この URL では、すべてのテンプレート変数を、ヒットから取得した値に置き換えます。例えばユーザーの前回のセッションの長さが 132 秒で、ユーザーが iOS SDK バージョン 4.6.0 を使用している場合には、生成される URL は次のようになります。

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
