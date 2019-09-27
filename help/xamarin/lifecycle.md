---
description: Android にライフサイクル指標を実装するための情報です。iOS では、ライフサイクル指標は自動的に収集されます。
keywords: Xamarin
seo-description: Android にライフサイクル指標を実装するための情報です。iOS では、ライフサイクル指標は自動的に収集されます。
seo-title: Implement lifecycle
solution: Marketing Cloud，開発者
title: ライフサイクルの実装
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

この情報は、Android用のライフサイクル指標の実装に役立ちます。

>[!TIP]
>
>iOS では、ライフサイクル指標は自動的に収集されます。

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

iOSでは、ライフサイクル指標が自動的に収集されます。

## Android

メインアクティビティで、Android SDKのアプリケーションコンテキストを設定します。

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
