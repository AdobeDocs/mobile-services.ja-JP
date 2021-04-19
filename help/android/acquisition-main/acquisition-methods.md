---
description: 'Android ライブラリでは、次の獲得メソッドが提供されています。 '
keywords: Android, ライブラリ, モバイル, SDK
seo-description: 'Android ライブラリでは、次の獲得メソッドが提供されています。 '
seo-title: 獲得メソッド
solution: Experience Cloud,Analytics
title: 獲得メソッド
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 100%

---

# 獲得メソッド {#acquisition-methods}

Android ライブラリでは、次の獲得メソッドが提供されています。

* **campaignStartForApp**

   アプリ獲得キャンペーンを、まるでユーザーがリンクをクリックしたかのような状況で開始できます。これは、手動で獲得リンクを作成し、自身でアプリストアへのリダイレクトを処理する場合に便利です。

   * このメソッドの構文を次に示します。

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
