---
description: Android ライブラリによって提供される Audience Manager メソッドのリストを示します。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: Audience Manager メソッド
topic-fix: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
exl-id: 707b40b8-e56e-4c26-8b59-87c5d71cad0c
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 100%

---

# Audience Manager メソッド{#audience-manager-methods}

Android ライブラリによって提供される Audience Manager メソッドのリストを示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。例えば、Experience Cloud ID メソッドのプレフィックスは、`audience manager` です。

Audience Manager が JSON ファイルに設定されている場合、ライフサイクル指標を含むシグナルがライフサイクルヒットと共に送信されます。

* **getVisitorProfile**

   最後に取得した訪問者プロファイルを返します。シグナルが送信されていない場合は `null` を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`SharedPreferences` に保存されます。

   * このメソッドの構文を次に示します。

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   現在の DPID を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void getDpid(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   現在の DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void getDpuuid(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   DPID と DPUUID を設定します。これらの値は各シグナルと共に送信されます。

   このメソッドに渡される DPUUID 値に URL セーフでない文字が含まれている場合、SDK に渡す前に、ユーザーはパラメーターをエンコードする必要があります。

   * このメソッドの構文を次に示します。

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Audience Management に特性を持つシグナルを送信し、ブロックコールバックで返された一致するセグメントを取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
