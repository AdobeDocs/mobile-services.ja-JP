---
description: 'Android ライブラリでは、次の獲得メソッドが提供されています。 '
keywords: Android, ライブラリ, モバイル, SDK
seo-description: 'Android ライブラリでは、次の獲得メソッドが提供されています。 '
seo-title: 獲得メソッド
solution: Experience Cloud,Analytics
title: 獲得メソッド
topic: 開発者と導入
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 獲得メソッド{#acquisition-methods}

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
