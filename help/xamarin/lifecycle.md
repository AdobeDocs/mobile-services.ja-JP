---
description: Android 用のライフサイクル指標の実装に役立つ情報です。 ライフサイクル指標は iOS 用に自動的に収集されます。
keywords: Xamarin
solution: Experience Cloud
title: ライフサイクルの実装
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# ライフサイクルの実装 {#implement-lifecycle}

この情報は、Android 用のライフサイクル指標の実装に役立ちます。

>[!TIP]
>
>ライフサイクル指標は iOS 用に自動的に収集されます。

ライフサイクルを実装した後、モバイルライブラリで自動的に測定できる指標とディメンションについては、[ ライフサイクル指標 ](/help/ios/metrics.md) を参照してください。

## iOS

iOS では、ライフサイクル指標が自動的に収集されます。

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
