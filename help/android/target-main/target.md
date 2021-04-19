---
description: Android アプリケーションでターゲットコンテンツを配信できます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: Android アプリケーションでターゲットコンテンツを配信できます。
seo-title: Target の設定
solution: Experience Cloud,Analytics
title: Target の設定
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
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
