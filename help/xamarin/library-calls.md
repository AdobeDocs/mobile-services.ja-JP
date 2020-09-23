---
description: スクリプトからプラグインを呼び出すのに役立つ情報です。
keywords: Xamarin
seo-description: スクリプトからプラグインを呼び出すのに役立つ情報です。
seo-title: ライブラリへの呼び出し
solution: Experience Cloud
title: ライブラリへの呼び出し
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 13%

---


# ライブラリへの呼び出し{#making-calls-to-the-library}

スクリプトからプラグインを呼び出すのに役立つ情報です。

スクリプトからプラグインを呼び出す場合は、名前空間を読み込む必要があります。

使用方法 `Com.Adobe.Mobile`:

* **iOS**:名前空間を読み込んだ後、クラス内の静的メソッドを使用してSDKを直接呼び出すことができ `ADBMobile` ます。

* **Android**:クラス内の静的メソッドを使用して、SDKを直接呼び出すことができ `Config/Analytics/Target/AudienceManager/Media`ます。

