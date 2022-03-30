---
description: スクリプトからライブラリプラグインを呼び出します。
keywords: Unity
solution: Experience Cloud Services
title: ライブラリへの呼び出し
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
exl-id: de95edd5-3a5b-4b84-aeea-adff3362f544
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 18%

---

# ライブラリへの呼び出し{#making-calls-to-the-library}

スクリプトからプラグインを呼び出す場合は、名前空間を読み込みます。

* **C#:** using `com.adobe.mobile;`

名前空間を読み込んだ後、ADBMobile クラスの静的メソッドを使用して、プラグインに対して直接呼び出しをおこなうことができます。
