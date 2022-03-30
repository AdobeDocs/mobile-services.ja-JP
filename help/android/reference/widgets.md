---
description: Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットはアプリケーションコンテキストをアプリと共有するので、ヒットの順序と訪問者 ID が保持されます。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud Services,Analytics
title: Android ウィジェット
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Android ウィジェット {#android-widgets}

Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットはアプリケーションコンテキストをアプリと共有するので、ヒットの順序と訪問者 ID が保持されます。

次のガイドラインは、Android ウィジェットの追跡に役立ちます。

* ウィジェットに、ライフサイクル指標（`startActivity`/`stopActivity`）呼び出しを実装しないでください。

* ウィジェットがいつホーム画面に追加されたかを追跡するには、`trackState` または `trackEvent` 呼び出しをウィジェットの `onEnabled` メソッドに追加します。

* アプリがいつウィジェットから起動されたかを追跡するには、アプリケーションを起動するインテントを作成する前に、`trackState` または `trackEvent` 呼び出しを追加します。

* アクションのコンテキストを追跡するには、各アクションを個別にセグメント化できるようにする `ContextData` 変数を定義します（例えば、`AppExperienceType="widget"` と `app`）。
