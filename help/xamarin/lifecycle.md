---
description: Android用のライフサイクル指標を実装するのに役立つ情報です。 ライフサイクル指標はiOS用に自動的に収集されます。
keywords: Xamarin
seo-description: Android用のライフサイクル指標を実装するのに役立つ情報です。 ライフサイクル指標はiOS用に自動的に収集されます。
seo-title: ライフサイクルの実装
solution: Experience Cloud
title: ライフサイクルの実装
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# ライフサイクルの実装 {#implement-lifecycle}

この情報は、Android向けのライフサイクル指標の導入に役立ちます。

>[!TIP]
>
>ライフサイクル指標はiOS用に自動的に収集されます。

ライフサイクルが実装された後、モバイルライブラリによって自動的に測定される指標とディメンションについては、 [ライフサイクル指標](/help/ios/metrics.md)（英語）を参照してください。

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
