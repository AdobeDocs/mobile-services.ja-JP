---
description: Android ライブラリによって提供される Experience Cloud ID メソッドを示します。
keywords: android;library;mobile;sdk
seo-description: Android ライブラリによって提供される Experience Cloud ID メソッドを示します。
seo-title: Adobe Experience Platform Identity Service methods
solution: Marketing Cloud,Analytics
title: Adobe Experience Platform Identity Service methods
topic: 開発者と導入
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 8fc515a6e89044b9dac98b3f207c5f43b658a2ec

---


# Adobe Experience Platform Identity Service methods{#experience-cloud-id-service-methods}

Android ライブラリによって提供される Experience Cloud ID メソッドを示します。

SDKは、現在、Analytics、Target、Audience ManagerおよびAdobe Experience Platform IDサービスを含む、複数のAdobe Experience cloudソリューションをサポートしています。

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   アドビ JavaScript ライブラリで使用するために、アドビ訪問者データを URL 文字列に追加します。このメソッドを使用するには、Mobile SDK 4.12 以降が必要です。詳しくは、[訪問者 ID ヘルパー関数の追加](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)を参照してください。

   >[!IMPORTANT]
   >
   >このメソッドは、ネットワーク呼び出しをブロックする原因となる可能性があります。 時間的制約があるスレッドでこのメソッドを呼び出さないでください。

   * このメソッドの構文を次に示します。

      ```java
      public static String appendToURL(final String URL) 
      ```

      訪問者情報が追加される、必須の URL 文字列。

   * このメソッドのコードサンプルを次に示します。

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   訪問者 ID サービスから Experience Cloud ID を取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static String getMarketingCloudId(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Experience Cloud ID を使用すると、各訪問者に関連付けることができる追加の顧客 ID を設定できます。訪問者 API は、同じ訪問者に対して複数の顧客 ID と、異なる顧客 ID の範囲を区別するための顧客タイプ識別子を受け取ります。このメソッドは、JavaScript ライブラリの `setCustomerIDs` に相当します。

   * このメソッドの構文を次に示します。

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   指定された識別子の型と値を訪問者 ID サービスに同期します。

   `authenticationState` を次のいずれかの値として渡します。

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * このメソッドの構文を次に示します。

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   指定された識別子を ID サービスに同期します。

   `authenticationState` を次のいずれかの値として渡します。
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * このメソッドの構文を次に示します。

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   読み取り専用の `ADBVisitorID` オブジェクトのリストを取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   バージョン4.16.0で導入されたこのメソッドは、訪問者IDサービスのURL変数を含む適切な形式の文字列を返します。 このメソッドの使用方法について詳しくは、 [Adobe Experience Platform IDサービスのメソッドを参照してください](/help/android/reference/hybrid-app.md)。

   * このメソッドの構文を次に示します。

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
