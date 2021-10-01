---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
solution: Experience Cloud,Analytics
title: ADBMobile JSON 設定パスのオーバーライド
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 100%

---

# ADBMobile JSON 設定パスのオーバーライド {#override-the-adbmobile-json-config-path}

アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。

`ADBMobile overrideConfigPath:filePath` メソッドを使用すると、アプリケーションの起動時に別の `ADBMobile.json` 設定ファイルのパスを指定できます。このメソッドは、`applicationDidFinishLaunchingWithOptions` メソッド内で呼び出す必要があります。また、このコールは、その他の Experience Cloud SDK コール（`collectLifecycleData` など）より前におこなう必要があります。

このメソッドを別のパスで呼び出すと、アプリケーションが終了するまで設定ファイルが一時的にオーバーライドされます。

以下に例を示します。

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```
