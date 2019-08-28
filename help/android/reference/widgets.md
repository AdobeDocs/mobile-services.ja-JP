---
description: Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。
keywords: android;library;mobile;sdk
seo-description: Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。
seo-title: Androidウィジェット
solution: Marketing Cloud、Analytics
title: Androidウィジェット
topic: 開発者と導入
uuid: 1a3718ff-967b-4c8e- ae0b- ba15bddbda0a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。

以下のガイドラインは、Android ウィジェットを追跡するのに役立ちます。

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* ウィジェットがいつホーム画面に追加されたかを追跡するには、`trackState` または `trackEvent` 呼び出しをウィジェットの `onEnabled` メソッドに追加します。

* アプリがいつウィジェットから起動されたかを追跡するには、アプリケーションを起動するインテントを作成する前に、`trackState` または `trackEvent` 呼び出しを追加します。

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

