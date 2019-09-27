---
description: スクリプトからプラグインを呼び出すための情報です。
keywords: Xamarin
seo-description: スクリプトからプラグインを呼び出すための情報です。
seo-title: ライブラリへの呼び出し
solution: Marketing Cloud,Developer
title: ライブラリへの呼び出し
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

This information to help you make calls to the plugin from your scripts.

スクリプトからプラグインを呼び出す場合、名前空間を読み込む必要があります。

By using :`Com.Adobe.Mobile`

* **iOS**:名前空間を読み込んだ後、クラス内の静的メソッドを使用してSDKを直接呼び出すことがで `ADBMobile` きます。

* **Android**:クラス内の静的メソッドを使用して、SDKを直接呼び出すことがで `Config/Analytics/Target/AudienceManager/Media`きます。

