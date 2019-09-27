---
description: 'Androidライブラリは、次の獲得方法を提供します '
keywords: android;library;mobile;sdk
seo-description: 'Androidライブラリは、次の獲得方法を提供します '
seo-title: 獲得メソッド
solution: Marketing Cloud,Analytics
title: 獲得メソッド
topic: 開発者と導入
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

Androidライブラリは、次の獲得方法を提供します。

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
