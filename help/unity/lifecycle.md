---
description: モバイルライブラリによって自動的に測定される指標およびディメンションを測定します
keywords: Unity
solution: Experience Cloud Services
title: ライフサイクルの実装
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# ライフサイクルの実装{#implement-lifecycle}

ライフサイクル実装後にモバイルライブラリで自動的に測定できる指標およびディメンションについて詳しくは、 [Android のライフサイクル指標](/help/android/metrics.md) または [iOSのライフサイクル](/help/ios/metrics.md).

## iOS

ライフサイクル指標は、iOSで自動的に収集されます。

## Android

Unity スクリプトで、Android SDK のアプリケーションコンテキストを設定します。 次のコードを `Awake()` FIRST シーンの関数：

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
