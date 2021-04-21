---
description: スクリプトからライブラリプラグインを呼び出します。
keywords: Unity
solution: Experience Cloud
title: ライブラリへの呼び出し
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
exl-id: de95edd5-3a5b-4b84-aeea-adff3362f544
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 18%

---

# ライブラリへの呼び出し{#making-calls-to-the-library}

スクリプトからプラグインを呼び出す場合は、次の名前空間を読み込みます。

* **C#:** 使用  `com.adobe.mobile;`

名前空間を読み込んだ後、ADBMobileクラスの静的メソッドを使用して、プラグインを直接呼び出すことができます。
