---
description: 次の表に、Android SDK および Adobe Mobile Services で使用される様々なアプリ識別子を示します。
solution: Experience Cloud Services,Analytics
title: アプリ ID
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# アプリ ID{#app-ids}

次の表に、Android SDK および Adobe Mobile Services で使用される様々なアプリ識別子を示します。

| ID | 説明 |
|--- |--- |
| ライフサイクル指標と共に送信される ID | アプリ名と、App Store に提出されるバンドルのバージョンを組み合わせたもの。この値は、Adobe Mobile Services のバージョンレポートで使用されます。この値を使用してフィルタリングして、アプリの特定のリリースバージョンでセグメント化することができます。 |
| App Store ID | この ID は、App Store によってアプリに割り当てられ、ダウンロード計測用リンク作成時に Adobe Mobile Services で提供されます。 |
| ADBMobile JSON 設定の AppID | これは、システム内の関連するすべてのメタデータについて、Adobe Mobile Services によってアプリインスタンスに割り当てられる一意の ID です。この ID は、獲得トラッキングまたは追跡リンクの一意の URL を作成するために使用されます。この ID は、このファイルを UI からダウンロードすると自動的に ADBMobile JSON 設定ファイルに追加され、アプリの獲得設定の「アプリ設定」に表示されます。 |
