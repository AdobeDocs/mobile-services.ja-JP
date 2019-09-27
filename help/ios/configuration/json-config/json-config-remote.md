---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-title: ADBMobile JSON設定パスの上書き
solution: Marketing Cloud,Analytics
title: ADBMobile JSON設定パスの上書き
topic: 開発者と導入
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. このメソッドは、`applicationDidFinishLaunchingWithOptions` メソッド内で呼び出す必要があります。また、このコールは、その他の Experience Cloud SDK コール（`collectLifecycleData` など）より前におこなう必要があります。

このメソッドを別のパスで呼び出すと、アプリケーションが閉じられるまで、設定ファイルの1回限りの上書きが発生します。

以下に例を示します。

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

