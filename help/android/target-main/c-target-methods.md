---
description: Android ライブラリによって提供される Adobe Target メソッドのリストを示します。
keywords: android;library;mobile;sdk
seo-description: Android ライブラリによって提供される Adobe Target メソッドのリストを示します。
seo-title: AndroidのTargetメソッド
solution: Marketing Cloud、Analytics
title: AndroidのTargetメソッド
topic: 開発者と導入
uuid: 8e9808b2- ba80-4646- ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# AndroidのTargetメソッド{#target-methods}

Android ライブラリによって提供される Adobe Target メソッドのリストを示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスなど、複数のAdobe Experience Cloudソリューションをサポートしています。Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[ライフサイクル指標](/help/android/metrics.md)は、各 mbox が読み込むパラメーターとして送信されます。

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**プロパティ：**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**文字列定数**

>[!TIP]
>
>次の定数は、カスタムパラメーターにキーを設定するときに使いやすくするためのものです。

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


* **loadRequest**

   設定した Target サーバーに request を送信し、ブロック callback で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   設定した Target サーバーに request を送信し、ブロック callback で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   設定した Target サーバーにリクエストを送信し、TargetCallback で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **戻り値：**&#x200B;なし

   * **パラメーター：**

      このメソッドのパラメーターを次に示します。

      * **name**

         取得する Target の mbox／ロケーションの名前。

         * **タイプ:** 文字列
      * **defaultContent**

         Target サーバーに到達できない場合、またはユーザーがキャンペーンの対象にならない場合にコールバックで返される値。

         * **タイプ:** 文字列
      * **profileParameters**

         この辞書の値は、Target へのリクエストの「profileParameters」オブジェクトに格納されます。

         * **タイプ:** マップ `<String, Object>`
      * **orderParameters**

         この辞書の値は、Target へのリクエストの「order」オブジェクトに格納されます。

         * **タイプ:** マップ `<String, Object>`
      * **mboxParameters**

         このディクショナリの値は、Targetにリクエストされます。

         * **タイプ:** マップ `<String, Object>`
      * **requestLocationParameters**

         この辞書の値は、Target へのリクエストの「requestLocation」オブジェクトに格納されます。

         * **タイプ:** マップ `<String, Object>`
      * **callback**

         このメソッドは、Target サーバーからのオファーのコンテンツで呼び出されます。Target サーバーに到達できない場合、またはユーザーがキャンペーンの対象にならない場合、defaultContent が返されます。

         * **タイプ:** targetCallback `<String>`
   * このメソッドのサンプルコードを次に示します。

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      基となる Target API について詳しくは、Target 開発者向けヘルプの[配信](https://docs.adobe.com/dev/products/target/reference/delivery.html)を参照してください。








* **createOrder&#x200B;ConfirmRequest**

   指定されたパラメーターで TargetLocationRequest オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   指定されたパラメーターで TargetLocationRequest オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   アプリから対象の cookie をクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void clearCookies();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   pcID を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static String getPcID();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   セッション ID を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static String getSessionID();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   サードパーティの ID を設定します。

   * このメソッドの構文を次に示します。

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   サードパーティの ID を返します。

   * このメソッドの構文を次に示します。

      ```java
      public static String getThirdPartyID();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
