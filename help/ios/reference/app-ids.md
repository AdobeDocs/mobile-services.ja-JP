---
description: 次の表に、iOS SDK および Adobe Mobile Services で使用される様々なアプリ識別子を示します。
solution: Experience Cloud Services,Analytics
title: アプリ ID
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# アプリ ID {#app-ids}

次の表に、iOS SDK および Adobe Mobile Services で使用される様々なアプリ識別子を示します。

| ID | 説明 |
|--- |--- |
| ライフサイクル指標と共に送信される ID | アプリ名と、App Store に提出されるバンドルのバージョンを組み合わせたもの。この値は、Adobe Mobile Services のバージョンレポートに使用されます。また、アプリの特定のリリースバージョンで結果をフィルタリングするのにも使用できます。 |
| App Store ID | この ID は、App Store によってアプリに割り当てられ、ダウンロード計測用リンク作成時に Adobe Mobile Services で提供されます。 |
| ADBMobile JSON 設定の AppID | この ID は、関連付けられているシステム内のすべてのメタデータ用に、Adobe Mobile Services がアプリインスタンスに割り当てる一意の ID です。この ID は、獲得の追跡または追跡リンク用の一意の URL の作成に使用され、UI からダウンロードされたとき、ADBMobile JSON 設定ファイルに自動的に追加されます。また、アプリの「アプリ設定」の「獲得」設定にも表示されます。 |
