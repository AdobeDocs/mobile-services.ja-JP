---
description: iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。
seo-title: Adobe Mobile Services の iOS Target メソッド
solution: Experience Cloud,Analytics
title: iOS の Target メソッド
topic: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 100%

---


# iOS の Target メソッド {#target-methods}

iOS ライブラリが提供する Adobe Target メソッドの一覧を以下に示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。メソッドには、ソリューションに応じたプレフィックスが付きます。例えば、Target メソッドの場合、プレフィックスは「`target`」です。

>[!TIP]
>
>ライフサイクル指標は、各 mbox が読み込むパラメーターとして送信されます。詳しくは、「[ライフサイクル指標](/help/ios/metrics.md)」を参照してください。Target リクエストを `didFinishLaunching` delegate メソッド内で送信する場合は、Target 実装コードの前に `[ADBMobile trackAction:data:]` または `[ADBMobile trackState:data:]` 呼び出しを追加します。これにより、Target リクエストには、完全なライフサイクルデータが含まれます。

## クラス参照：ADBTargetLocationRequest

### プロパティ

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### 文字列定数

>[!TIP]
>
>次の定数は、カスタムパラメーターのキーを設定するのに便利です。

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
>* バージョン 4.14.0 より&#x200B;**前の** SDK を使用している場合、パラメーターの制限については、「[Input Parameters](https://developers.adobetarget.com/api/#input-parameters)」を参照してください。
   >
   >
* SDK バージョン 4.14.0 **以降**&#x200B;の SDK を使用している場合、パラメーターの制限については、「[Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters)」を参照してください。


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

      基になる Target API について詳しくは、[Adobe Target Developers](https://docs.adobe.com/dev/products/target/reference/delivery.html) を参照してください。







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

   `ADBTargetLocationRequest` を作成します。

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
   >SDK バージョン 4.10.0 以降、Target で cookie は使用されていません。このメソッドは、thirdPartyID と sessionID をリセットします。

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
