---
description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-description: アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。
seo-title: ADBMobile JSON 設定パスのオーバーライド
solution: Marketing Cloud、Analytics
title: ADBMobile JSON 設定パスのオーバーライド
topic: 開発者と導入
uuid: 6872a5d7-0c5a-4fdc- b7bf- ad1534763a6a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

アプリケーションの起動時に、別の ADBMobile JSON 設定ファイルを読み込むことができます。

`Config.overrideConfigStream(configInput)` このメソッドを使用すると、アプリケーションの起動時に `ADBMobile.json` 異なる設定ファイルへのパスを指定できます。This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

このメソッドを別のパスで呼び出すと、アプリケーションが終了するまで設定ファイルが一時的にオーバーライドされます。

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

