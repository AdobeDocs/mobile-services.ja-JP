---
description: Adobe Target のプリフェッチ機能では、iOS Mobile SDK がサーバーからの応答をキャッシュするので、可能な限り少ない回数で効率良くオファーコンテンツを取得できるようになります。
seo-description: Adobe Target のプリフェッチ機能では、iOS Mobile SDK がサーバーからの応答をキャッシュするので、可能な限り少ない回数で効率良くオファーコンテンツを取得できるようになります。
seo-title: iOS でのオファーコンテンツのプリフェッチ
title: iOS でのオファーコンテンツのプリフェッチ
uuid: fef58042-65e2-4579- b8f1- d21554d2af57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# iOS でのオファーコンテンツのプリフェッチ {#prefetch-offer-content-in-ios}

Adobe Target のプリフェッチ機能では、iOS Mobile SDK がサーバーからの応答をキャッシュするので、可能な限り少ない回数で効率良くオファーコンテンツを取得できるようになります。

>[!IMPORTANT]
>
>iOS用のモバイルSDKのプリフェッチ機能は、Adobe Targetの自動ターゲット、自動割り当ておよび自動パーソナライゼーションアクティビティタイプではサポートされていません。

このプロセスにより、読み込み時間が短縮され、複数のネットワーク呼び出しが回避されるほか、モバイルアプリユーザーがどの mbox を訪問したかを Adobe Target に通知することができます。プリフェッチ呼び出し中にすべてのコンテンツが取得され、キャッシュされます。このコンテンツは、指定された mbox 名のキャッシュされたコンテンツを含む今後のすべての呼び出しに対してキャッシュから取得されます。

プリフェッチコンテンツは、起動間で保持されません。The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

SDK バージョン 4.14 以降で、`environmentId``ADBMobileConfig.json` が指定されている場合、v2 バッチ mbox TnT 呼び出しを開始すると、 ファイルから environmentId を取得します。このファイルで `environmentId` が指定されていない場合、TNT バッチ mbox 呼び出しで環境パラメーターは送信されず、オファーはデフォルト環境に配信されます。

以下に例を示します。

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## プリフェッチメソッド {#section_05967F1F3A554B0FBC2C08A954554BDE}

iOS でのプリフェッチに使用できるメソッドを以下に示します。

* **targetPrefetchContent**

   設定されている Target サーバーに、ロケーションの配列と共にプリフェッチの要求を送信し、指定されたコールバックで要求ステータスを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * このメソッドのパラメーターを次に示します。

      * **`targetPrefetchArray`**

         プリフェッチする各 Target のロケーションの名前と mboxParameters を含む `TargetPrefetchObjects` の配列。

      * **`profileParameters`**

         この要求のすべてのロケーションプリフェッチで使用されるプロファイルパラメーターのキーと値が含まれます。

      * **`callback`**

         プリフェッチの完了時に呼び出されます。Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

   リクエスト配列に指定された複数の mbox の場所に対してバッチリクエストを実行します。配列内の各オブジェクトにはコールバック関数が含まれています。コールバック関数は、指定したmboxの場所でコンテンツが利用可能になったときに呼び出されます。

   >[!IMPORTANT]
   >
   >要求された場所のコンテンツが既にキャッシュされている場合、指定されたコールバックで即座に返されます。コンテンツがキャッシュされていない場合は、SDK は Target サーバーにネットワーク要求を送信してコンテンツを取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * このメソッドのパラメーターを次に示します。

      * **`requests`**

         取得するロケーションごとに、名前、デフォルトコンテンツ、パラメーターおよびコールバック関数を含む `TargetRequestObjects` の配列。

      * **`profileParameters`**

         このリクエストのすべての場所でのプリフェッチで使用するプロファイルパラメーターのキーと値を含みます。

* **targetPrefetchClearCache**

   Target プリフェッチによってキャッシュされたデータをクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * このメソッドのパラメーターはありません。

* **targetRequestObjectWithName**

   指定されたデータを使用して `TargetRequestObject` のインスタンスを作成し、返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * このメソッドのパラメーターはありません。

* **createTargetPrefetchObject**

   指定されたデータを使用して `TargetPrefetchObject` のインスタンスを作成し、返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

iOS でプリフェッチをサポートするパブリッククラスを以下に示します。

### クラスリファレンス:targetPrefsオブジェクト

mbox 名と、mbox のプリフェッチで使用されるパラメーターをカプセル化します。

* **`name`**

   取得する場所/mboxの名前。

   * **型：** NSString*

* **`mboxParameters`**

   mbox パラメーターのキーと値のペアを含むオプションの辞書。

   * **型：** NSDictionary*

* **`orderParameters`**

   注文パラメーターのキーと値のペアを含む辞書。

   * **型：** NSDictionary*

* **`productParameters`**

   製品パラメーターのキーと値のペアを含む辞書。

   * **型：** NSDictionary*

### クラスリファレンス:targetRequestObject

このクラスは、mbox 名、デフォルトコンテンツ、mbox パラメーターおよび Target ロケーションの要求に使用されるリターンコールバックをカプセル化します。

* **`name`**

   要求されるロケーションの名前。

   * **型：** NSString*

* **`mboxParameters`**

   取得する場所／mbox の名前を表す NSString 値。

   * **型：** NSString*

* **`defaultContent`**

   Target サーバーが到達不能な場合に返されるデフォルトのコンテンツ。

   * **型：** NSString*

* **`callback`**

   バッチが Target の場所をリクエストすると、この場所でコンテンツが利用できる場合にコールバックが呼び出されます。

   * **型：** Function

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

iOS SDK を使用したコンテンツのプリフェッチ方法の例を以下に示します。

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

iOS SDK を使用したバッチ `loadRequest` の例を以下に示します。

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## 追加情報 {#section_A454BAD1CD49423E86C71BAEE06125FD}

以下は、これらのサンプルの関連情報です。

* `ProductParameters` でのみ、以下のキーを使用できます。

   * `id`
   * `categoryId`

* `OrderParameters` でのみ、以下のキーを使用できます。

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` は、文字列の配列を受け取ります。