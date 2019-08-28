---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-title: ADBMobile JSON configパスの上書き
solution: Marketing Cloud、Analytics
title: ADBMobile JSON configパスの上書き
topic: 開発者と導入
uuid: 0d1be674- c634-4a48- aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。

`ADBMobile overrideConfigPath:filePath` このメソッドを使用すると、アプリケーションの起動時に `ADBMobile.json` 異なる設定ファイルへのパスを指定できます。このメソッドは、`applicationDidFinishLaunchingWithOptions` メソッド内で呼び出す必要があります。また、このコールは、その他の Experience Cloud SDK コール（`collectLifecycleData` など）より前におこなう必要があります。

別のパスでこのメソッドを呼び出すと、アプリケーションを閉じるまで設定ファイルの一時的な上書きが発生します。

以下に例を示します。

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

