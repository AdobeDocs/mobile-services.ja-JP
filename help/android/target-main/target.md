---
description: Android アプリケーションでターゲットコンテンツを配信できます。
keywords: android;library;mobile;sdk
seo-description: Android アプリケーションでターゲットコンテンツを配信できます。
seo-title: Target の設定
solution: Experience Cloud,Analytics
title: Target の設定
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 100%

---


# Target の設定 {#target-configuration}

Android アプリケーションでターゲットコンテンツを配信できます。

## アプリケーションコンテキストの設定 {#section_37CAE496FF894FCA821F7760605574CA}

**（必須）**`setContext()` メソッドは、メインアクティビティの `onCreate()` メソッドで 1 回呼び出す必要があります。

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
