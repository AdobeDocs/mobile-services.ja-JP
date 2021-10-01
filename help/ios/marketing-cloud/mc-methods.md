---
description: iOS ライブラリが提供する Adobe Experience Platform サービスメソッドを以下に示します。
solution: Experience Cloud,Analytics
title: Adobe Experience Platform ID サービスのメソッド
topic-fix: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
exl-id: 82a246fc-f679-4fa5-b9c0-dc909a7e7d93
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 96%

---

# Adobe Experience Platform ID サービスのメソッド {#experience-cloud-id-service-methods}

iOS ライブラリが提供する Adobe Experience Platform サービスメソッドを以下に示します。

SDK は現在、Analytics、Target、Audience Manager、Experience Cloud ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。

メソッドには、ソリューションに応じたプレフィックスが付きます。Experience Cloud ID メソッドの場合、プレフィックスは「`visitor`」です。詳しくは、[Experience Cloud ID の有効化](/help/ios/marketing-cloud/mcvid.md)を参照してください。

* **`+`(nullable NSURL `*`)visitorAppendToURL:(nullable NSURL `*`)url;**

   アドビ JavaScript ライブラリで使用するために、アドビ訪問者データを URL 文字列に追加します。このメソッドを使用するには、Mobile SDK 4.12 以降が必要です。詳しくは、 Adobe Experience Cloud ID サービスのドキュメントの [appendVisitorIDsTo](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/appendvisitorid.html?lang=ja) を参照してください。

   >[!IMPORTANT]
   >
   >このメソッドにより、ネットワークブロック呼び出しがおこなわれる可能性があります。時間的制約があるスレッドでこのメソッドを呼び出さないでください。

   * 訪問者情報を追加する必須の `URL<NSURL>` 文字列。
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
      >このメソッドは、ネットワークブロック呼び出しがおこなわれる可能性があるので、UI スレッドから呼び出さ&#x200B;**ない**&#x200B;でください。

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

   指定された識別子の型と値を ID サービスに同期します。`authState` を次のいずれかの値として渡します。

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

* **visitorgetUrlVariablesAsync**

   バージョン 4.16.0 で導入されたこのメソッドは、訪問者 ID サービスの URL 変数を含む適切な形式の文字列を返します。このメソッドの使用方法について詳しくは、「[Adobe Experience Platform ID サービスメソッド](/help/ios/reference/hybrid-app.md)」を参照してください。

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

## ADBMobileVisitorAuthenticationState enum  {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```
