---
description: Audience Management からシグナルを送信し、訪問者セグメントを獲得することができます。
keywords: android;library;mobile;sdk
seo-description: Audience Management からシグナルを送信し、訪問者セグメントを獲得することができます。
seo-title: Audience Manager configuration
solution: Marketing Cloud,Analytics
title: Audience Managerの設定
topic: 開発者と導入
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

シグナルを送信し、Audience Managerから訪問者セグメントを取得できます。

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Required) The  method must be called once in the  method of your main activity.**`setContext()``onCreate()`

このメソッドのコードサンプルを次に示します。

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

AnalyticsまたはTargetの実装時にこのメソッド呼び出しを追加した場合は、再度追加する必要はありません。
