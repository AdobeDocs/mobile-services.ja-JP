---
description: Android アプリケーションでターゲットコンテンツを配信できます。
keywords: android;library;mobile;sdk
seo-description: Android アプリケーションでターゲットコンテンツを配信できます。
seo-title: Targetの設定
solution: Marketing Cloud、Analytics
title: Targetの設定
topic: 開発者と導入
uuid: 09fe2c9c-7b60-49c3- bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Android アプリケーションでターゲットコンテンツを配信できます。

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**（必須）** メイン `setContext()` アクティビティの `onCreate()` メソッドでメソッドを1回呼び出す必要があります。

以下に例を示します。

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Analytics または Audience Management を実装したときに既にこのメソッド呼び出しを追加している場合は、再度追加する必要はありません。
