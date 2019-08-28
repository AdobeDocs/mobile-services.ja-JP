---
description: スクリプトからプラグインを呼び出すための情報です。
keywords: Xamarin
seo-description: スクリプトからプラグインを呼び出すための情報です。
seo-title: ライブラリへの呼び出し
solution: Marketing Cloud，開発者
title: ライブラリへの呼び出し
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

この情報は、スクリプトからプラグインを呼び出す際に役立ちます。

スクリプトからプラグインを呼び出す場合、名前空間を読み込む必要があります。

使用方法 `Com.Adobe.Mobile`:

* **iOS**:名前空間を読み込んだ後、 `ADBMobile` クラス内の静的メソッドを使用してSDKを直接呼び出すことができます。

* **Android**:SDKを直接呼び出すには `Config/Analytics/Target/AudienceManager/Media`、クラス内の静的メソッドを使用します。

