---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ライフサイクルの実装
solution: Marketing Cloud，開発者
title: ライフサイクルの実装
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# ライフサイクルの実装{#implement-lifecycle}

ライフサイクルの実装後にモバイルライブラリによって自動的に測定される指標とディメンションについて詳しくは、Androidのライフサイクル指標または [iOSのライフサイクル](/help/android/metrics.md) ( [Lifecycle Metrics)を参照してください](/help/ios/metrics.md)。

## iOS

ライフサイクル指標はiOSで自動的に収集されます。

## Android

Unity スクリプトで、Android SDK のアプリケーションコンテキストを設定します。Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

ライフサイクル指標を収集するには、すべてのシーンスクリプトに次のコードを追加します。

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

