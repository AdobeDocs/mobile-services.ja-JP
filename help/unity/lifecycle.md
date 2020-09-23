---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ライフサイクルの実装
solution: Experience Cloud
title: ライフサイクルの実装
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# ライフサイクルの実装{#implement-lifecycle}

ライフサイクルを実装した後、モバイルライブラリによって自動的に測定される指標とディメンションについて詳しくは、Androidの [ライフサイクル指標](/help/android/metrics.md) (Lifecycle Metrics in Android [)またはiOSの](/help/ios/metrics.md)ライフサイクル(Lifecycle)を参照してください。

## iOS

ライフサイクル指標はiOSで自動的に収集されます。

## Android

Unityスクリプトで、Android SDKのアプリケーションコンテキストを設定します。 最初のシーンの `Awake()` 関数に対する追加次のコード：

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

