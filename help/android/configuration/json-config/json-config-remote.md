---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
solution: Experience Cloud,Analytics
title: ADBMobile JSON 設定パスのオーバーライド
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# ADBMobile JSON 設定パスのオーバーライド {#override-the-adbmobile-json-config-path}

アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。

`Config.overrideConfigStream(configInput)` メソッドを使用すると、アプリケーションの起動時に別の `ADBMobile.json` 設定ファイルのパスを指定できます。このメソッドは、他の Experience Cloud SDK 呼び出しの前（`Config.collectLifecycleData()` の前）に、通常は最初にロードされたアクティビティの `onCreate` メソッドで呼び出す必要があります。

このメソッドを別のパスで呼び出すと、アプリケーションが終了するまで設定ファイルが一時的にオーバーライドされます。

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
