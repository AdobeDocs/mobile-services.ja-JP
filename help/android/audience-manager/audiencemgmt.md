---
description: Audience Management からシグナルを送信し、訪問者セグメントを獲得することができます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: Audience Management からシグナルを送信し、訪問者セグメントを獲得することができます。
seo-title: Audience Manager の設定
solution: Experience Cloud,Analytics
title: Audience Manager の設定
topic: 開発者と導入
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager の設定{#audience-manager-configuration}

Audience Manager からシグナルを送信し、訪問者セグメントを獲得することができます。

## アプリケーションコンテキストの設定 {#section_37CAE496FF894FCA821F7760605574CA}

**（必須）**`setContext()` メソッドは、メインアクティビティの `onCreate()` メソッドで 1 回呼び出す必要があります。

このメソッドのコードサンプルを次に示します。

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Analytics または Target を実装したときにこのメソッド呼び出しを追加している場合は、再度追加する必要はありません。
