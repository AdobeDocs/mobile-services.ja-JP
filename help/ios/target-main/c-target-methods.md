---
description: iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。
seo-title: Adobe Mobile ServicesのiOS Targetメソッド
solution: Marketing Cloud、Analytics
title: iOSのTargetメソッド
topic: 開発者と導入
uuid: 692bcda1-02ba-4902- bd65-15888adf1952
translation-type: tm+mt
source-git-commit: 8dc075603544aaab7fdedb1ff10a12f7fa7e21f5

---


# iOSのTargetメソッド {#target-methods}

iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスを含む複数のAdobe Experience Cloudソリューションをサポートしています。メソッドには、ソリューションに応じたプレフィックスが付きます。例えば、 メソッドの場合、プレフィックスは「`target`target」です。

>[!TIP]
>
>ライフサイクル指標は、各 mbox が読み込むパラメーターとして送信されます。詳しくは、[ライフサイクル指標](/help/ios/metrics.md)を参照してください。`didFinishLaunching` delegateメソッド内でTargetリクエストを送信する場合は、Target実装コードの前に、また `[ADBMobile trackAction:data:]` は `[ADBMobile trackState:data:]` 呼び出しを追加します。これにより、Targetリクエストに完全なライフサイクルデータが含まれます。

## クラスリファレンス:ADBTargetLocationRequest

### プロパティ

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### String constants

>[!TIP]
>
>The following constants are for ease of use when you set keys for custom parameters.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* If you are using SDKs **before** version 4.14.0, see [Input Parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or after**, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


### メソッド

* **targetLoadRequest:&#x200B;callback**

   設定した Target サーバーに request を送信し、ブロック `callback` で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   設定した Target サーバーにリクエストを送信し、生成されたオファーの文字列値をブロック callback に返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * 戻り値：なし

   * このメソッドのパラメーターを次に示します。

      * **`name`**

         取得する Target の mbox／ロケーションの名前。

         * **型：** NSString*
      * **`defaultContent`**

         Target サーバーに到達できない場合、またはユーザーがキャンペーンの対象にならない場合にコールバックで返される値。

         * **型：** NSString*
      * **`profileParameters`**

         この辞書の値は、Target へのリクエストの「profileParameters」オブジェクトに格納されます。

         * **型：** NSDictionary*
      * **`orderParameters`**

         この辞書の値は、Target へのリクエストの「order」オブジェクトに格納されます。

         * **型：** NSDictionary
      * **`mboxParameters`**

         この辞書の値は、Target へのリクエストの「mboxParameters」オブジェクトに格納されます。

         * **型：** NSDictionary*
      * **`requestLocationParameters`**

         この辞書の値は、Target へのリクエストの「requestLocation」オブジェクトに格納されます。

         **型：** NSDictionary*

      * **`callback`**

         このメソッドは、Target サーバーからのオファーのコンテンツで呼び出されます。Target サーバーに到達できない場合またはユーザーにキャンペーンの資格がない場合は、defaultContent が返されます。
      **型：** Function

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      基本的なTarget APIについて詳しくは、 [Adobe Target開発者](https://docs.adobe.com/dev/products/target/reference/delivery.html)を参照してください。







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   設定した Target サーバーに request を送信し、ブロック callback で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   を作成 `ADBTargetLocationRequest`します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   指定したパラメーターを持つ ADBTargetLocationRequest オブジェクトを作成する便利なコンストラクターです。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   サードパーティの ID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   サードパーティの ID を設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   アプリから対象の cookie をクリアします。

   >[!TIP]
   >
   >このメソッドは、thirdPartyID と sessionID をリセットします。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) targetClearCookies;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   PcID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   SessionID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### 例

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
