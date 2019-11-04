---
description: Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。
keywords: Android, ライブラリ, モバイル, SDK
seo-description: Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。
seo-title: Android ウィジェット
solution: Experience Cloud,Analytics
title: Android ウィジェット
topic: 開発者と導入
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android ウィジェット {#android-widgets}

Android ウィジェットは、アプリと同じメソッドを使用して追跡できます。ウィジェットは、アプリケーションコンテキストをアプリと共有するので、ヒットの順番および訪問者 ID は保持されます。

以下のガイドラインは、Android ウィジェットを追跡するのに役立ちます。

* ウィジェットに、ライフサイクル指標（`startActivity`/`stopActivity`）呼び出しを実装しないでください。

* ウィジェットがいつホーム画面に追加されたかを追跡するには、`trackState` または `trackEvent` 呼び出しをウィジェットの `onEnabled` メソッドに追加します。

* アプリがいつウィジェットから起動されたかを追跡するには、アプリケーションを起動するインテントを作成する前に、`trackState` または `trackEvent` 呼び出しを追加します。

* アクションのコンテキストを追跡するには、各アクションを個別にセグメント化できるようにする `ContextData` 変数を定義します（例えば、`AppExperienceType="widget"` と `app`）。

