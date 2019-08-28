---
description: Android ライブラリによって提供される Audience Manager メソッドのリストを示します。
keywords: android;library;mobile;sdk
seo-description: Android ライブラリによって提供される Audience Manager メソッドのリストを示します。
seo-title: Audience Managerメソッド
solution: Marketing Cloud、Analytics
title: Audience Managerメソッド
topic: 開発者と導入
uuid: 2f6e4664-1306-41d4-9fa7- e3a99f1df4ab
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

Android ライブラリによって提供される Audience Manager メソッドのリストを示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスを含む複数のAdobe Experience Cloudソリューションをサポートしています。Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

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

   このメソッドに渡されるDPUUID値にURLセーフでない文字が含まれている場合、顧客はパラメーターをエンコードしてからSDKに渡す必要があります。

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
