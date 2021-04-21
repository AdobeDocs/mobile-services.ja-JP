---
description: モバイルライブラリによって自動的に測定される指標とディメンションを測定します。
keywords: Unity
solution: Experience Cloud
title: ライフサイクルの実装
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# ライフサイクルの実装{#implement-lifecycle}

ライフサイクルの実装後、モバイルライブラリによって自動的に測定される指標とディメンションについて詳しくは、[Androidのライフサイクル指標](/help/android/metrics.md)または[iOSのライフサイクル](/help/ios/metrics.md)を参照してください。

## iOS

ライフサイクル指標はiOSで自動的に収集されます。

## Android

Unityスクリプトで、Android SDKのアプリケーションコンテキストを設定します。 最初の追加シーンの`Awake()`関数に対する次のコード：

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
