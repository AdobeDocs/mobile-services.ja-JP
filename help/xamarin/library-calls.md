---
description: スクリプトからプラグインを呼び出すのに役立つ情報です。
keywords: Xamarin
solution: Experience Cloud
title: ライブラリへの呼び出し
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# ライブラリへの呼び出し{#making-calls-to-the-library}

スクリプトからプラグインを呼び出すのに役立つ情報です。

スクリプトからプラグインを呼び出す場合は、名前空間を読み込む必要があります。

`Com.Adobe.Mobile` を使用：

* **iOS**:名前空間を読み込むと、クラスの静的メソッドを使用して SDK を直接呼び出すことがで `ADBMobile` きます。

* **Android**:クラスの静的メソッドを使用して、SDK を直接呼び出すことがで `Config/Analytics/Target/AudienceManager/Media`きます。
