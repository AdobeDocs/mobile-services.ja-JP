---
description: Android のライフサイクル指標を実装する際に役立つ情報です。 ライフサイクル指標は、iOSで自動的に収集されます。
keywords: Xamarin
solution: Experience Cloud Services
title: ライフサイクルの実装
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# ライフサイクルの実装 {#implement-lifecycle}

この情報は、Android のライフサイクル指標を実装する場合に役立ちます。

>[!TIP]
>
>ライフサイクル指標は、iOSで自動的に収集されます。

ライフサイクル実装後にモバイルライブラリで自動的に測定できる指標およびディメンションについては、 [ライフサイクル指標](/help/ios/metrics.md).

## iOS

iOSでは、ライフサイクル指標は自動的に収集されます。

## Android

メインアクティビティで、Android SDK のアプリケーションコンテキストを設定します。

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

すべてのアクティビティで、ライフサイクル呼び出しを実装します。

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
