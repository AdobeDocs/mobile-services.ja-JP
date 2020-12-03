---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-title: ADBMobile JSON 設定パスのオーバーライド
solution: Experience Cloud,Analytics
title: ADBMobile JSON 設定パスのオーバーライド
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '120'
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

