---
description: Android SDK および Adobe Mobile Services で使用される様々なアプリ識別子を次の表に示します。
seo-description: Android SDK および Adobe Mobile Services で使用される様々なアプリ識別子を次の表に示します。
seo-title: アプリ ID
solution: Marketing Cloud,Analytics
title: アプリ ID
topic: 開発者と導入
uuid: 3ac99489-6269-439e-a814-24102ef220b1
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# アプリ ID{#app-ids}

Android SDK および Adobe Mobile Services で使用される様々なアプリ識別子を次の表に示します。

| ID | 説明 |
|--- |--- |
| ライフサイクル指標と共に送信される ID | アプリ名と、App Store に提出されるバンドルのバージョンを組み合わせたもの。この値は、Adobe Mobile Services のバージョンレポートで使用されます。この値を使用してフィルタリングして、アプリの特定のリリースバージョンでセグメント化することができます。 |
| App Store ID | このIDは、アプリストアによってアプリに割り当てられ、ダウンロード計測用リンクを作成する際にAdobe mobileサービスで提供されます。 |
| ADBMobile JSON 設定の AppID | これは、システム内の関連するすべてのメタデータについて、Adobe Mobile Services によってアプリインスタンスに割り当てられる一意の ID です。この ID は、獲得トラッキングまたは追跡リンクの一意の URL を作成するために使用されます。この ID は、このファイルを UI からダウンロードすると自動的に ADBMobile JSON 設定ファイルに追加され、アプリの獲得設定の「アプリ設定」に表示されます。 |