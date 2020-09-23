---
description: Androidウィジェットは、アプリと同じメソッドを使用して追跡できます。 ウィジェットはアプリケーションコンテキストをアプリと共有するので、ヒットの順序と訪問者IDは保持されます。
keywords: android;library;mobile;sdk
seo-description: Androidウィジェットは、アプリと同じメソッドを使用して追跡できます。 ウィジェットはアプリケーションコンテキストをアプリと共有するので、ヒットの順序と訪問者IDは保持されます。
seo-title: Android ウィジェット
solution: Experience Cloud,Analytics
title: Android ウィジェット
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 46%

---


# Android ウィジェット {#android-widgets}

Androidウィジェットは、アプリと同じメソッドを使用して追跡できます。 ウィジェットはアプリケーションコンテキストをアプリと共有するので、ヒットの順序と訪問者IDは保持されます。

次のガイドラインは、Androidウィジェットの追跡に役立ちます。

* ウィジェットに、ライフサイクル指標（`startActivity`/`stopActivity`）呼び出しを実装しないでください。

* ウィジェットがいつホーム画面に追加されたかを追跡するには、`trackState` または `trackEvent` 呼び出しをウィジェットの `onEnabled` メソッドに追加します。

* アプリがいつウィジェットから起動されたかを追跡するには、アプリケーションを起動するインテントを作成する前に、`trackState` または `trackEvent` 呼び出しを追加します。

* アクションのコンテキストを追跡するには、各アクションを個別にセグメント化できるようにする `ContextData` 変数を定義します（例えば、`AppExperienceType="widget"` と `app`）。

