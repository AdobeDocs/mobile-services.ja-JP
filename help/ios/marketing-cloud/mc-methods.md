---
description: iOSライブラリから提供されるAdobe Experience Platform Identity Serviceメソッドを次に示します。
seo-description: iOSライブラリから提供されるAdobe Experience Platform Identity Serviceメソッドを次に示します。
seo-title: Adobe Experience Platform IDサービスのメソッド
solution: Marketing Cloud、Analytics
title: Adobe Experience Platform IDサービスのメソッド
topic: 開発者と導入
uuid: cdd307bc-8b7d-47a8- b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Adobe Experience Platform IDサービスのメソッド {#experience-cloud-id-service-methods}

iOSライブラリから提供されるAdobe Experience Platform Identity Serviceメソッドを次に示します。

SDK は現在、Analytics、Target、Audience Manager、Experience Cloud ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. 詳しくは、[Experience Cloud ID の有効化](/help/ios/marketing-cloud/mcvid.md)を参照してください。

* **`+`（nullable NSURL`*`） visitorAppendToURL:（nullable NSURL`*`） url;**

   アドビ JavaScript ライブラリで使用するために、アドビ訪問者データを URL 文字列に追加します。このメソッドを使用するには、モバイルSDKバージョン4.12以降が必要です。詳しくは、[訪問者 ID ヘルパー関数の追加](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)を参照してください。

   >[!IMPORTANT]
   >
   >このメソッドは、ブロックネットワーク呼び出しを引き起こす可能性があります。時間的制約があるスレッドでこのメソッドを呼び出さないでください。

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`訪問者情報が追加された文字列。

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Experience Cloud ID を ID サービスから取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Experience Cloud ID を使用すると、各訪問者に関連付けることができる追加の顧客 ID を設定できます。訪問者 API は、同じ訪問者に対して複数の顧客 ID と、異なる顧客 ID の範囲を区別するための顧客タイプ識別子を受け取ります。このメソッドは、JavaScript ライブラリの `setCustomerIDs` に相当します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   指定された識別子を ID サービスに同期します。`authState` を次のいずれかの値として渡します。

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   指定された識別子の型と値を ID サービスに同期します。Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * このメソッドの構文を次に示します。

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   読み取り専用の `ADBVisitorID` オブジェクトの配列を取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorGetURLVariablesAsync**

   バージョン4.16.0で導入されたこのメソッドは、訪問者IDサービスURL変数を含む適切な形式の文字列を返します。このメソッドの使用方法について詳しくは [、Adobe Experience Platform Identity Serviceメソッド](/help/ios/reference/hybrid-app.md)を参照してください。

   * このメソッドの構文を次に示します。

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID インターフェイス {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**パブリックメソッド：**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

