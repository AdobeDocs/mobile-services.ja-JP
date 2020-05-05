---
description: Android ライブラリによって提供される Experience Cloud ID メソッドを示します。
keywords: android;library;mobile;sdk
seo-description: Android ライブラリによって提供される Experience Cloud ID メソッドを示します。
seo-title: Adobe Experience Platform ID サービスのメソッド
solution: Marketing Cloud,Analytics
title: Adobe Experience Platform ID サービスのメソッド
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Adobe Experience Platform ID サービスのメソッド{#experience-cloud-id-service-methods}

Android ライブラリによって提供される Experience Cloud ID メソッドを示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。

これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。例えば、Experience Cloud ID メソッドのプレフィックスは、`visitor` です。詳しくは、「[Experience Cloud ID の設定](/help/android/c-marketing-cloud/mcvid.md)」を参照してください。

* **public static String appendToURL(final String URL)**

   アドビ JavaScript ライブラリで使用するために、アドビ訪問者データを URL 文字列に追加します。このメソッドを使用するには、Mobile SDK 4.12以降が必要です。 詳しくは、[訪問者 ID ヘルパー関数の追加](https://docs.adobe.com/content/help/ja-JP/id-service/using/id-service-api/methods/appendvisitorid.html)を参照してください。

   >[!IMPORTANT]
   >
   >このメソッドにより、ネットワークブロック呼び出しがおこなわれる可能性があります。時間的制約があるスレッドでこのメソッドを呼び出さないでください。

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
      >このメソッドは、ネットワークブロック呼び出しがおこなわれる可能性があるので、UI スレッドから呼び出さ&#x200B;**ない**&#x200B;でください。

* **syncIdentifiers**

   Experience Cloud IDを使用して、各訪問者に関連付けることができる追加の顧客IDを設定できます。 訪問者 API は、同じ訪問者に対して複数の顧客 ID と、異なる顧客 ID の範囲を区別するための顧客タイプ識別子を受け取ります。このメソッドは、JavaScript ライブラリの `setCustomerIDs` に相当します。

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

   バージョン 4.16.0 で導入されたこのメソッドは、訪問者 ID サービスの URL 変数を含む適切な形式の文字列を返します。このメソッドの使用方法について詳しくは、「[Adobe Experience Platform ID サービスメソッド](/help/android/reference/hybrid-app.md)」を参照してください。

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

## パブリックメソッド {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
