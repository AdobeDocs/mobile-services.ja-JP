---
description: スクリプトからプラグインを呼び出すのに役立つ情報です。
keywords: Xamarin
solution: Experience Cloud Services
title: ライブラリへの呼び出し
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# ライブラリへの呼び出し{#making-calls-to-the-library}

スクリプトからプラグインを呼び出すのに役立つ情報です。

スクリプトからプラグインを呼び出す場合は、名前空間を読み込む必要があります。

次を使用： `Com.Adobe.Mobile`:

* **iOS**:名前空間を読み込んだ後、 `ADBMobile` クラス。

* **Android**:静的メソッド ( `Config/Analytics/Target/AudienceManager/Media`クラス。
