---
description: Adobe Target のプリフェッチ機能では、サーバーからの応答をキャッシュすることで、Android Mobile SDK を使用して可能な限り少ない回数でオファーコンテンツを取得できます。
seo-description: Adobe Target のプリフェッチ機能では、サーバーからの応答をキャッシュすることで、Android Mobile SDK を使用して可能な限り少ない回数でオファーコンテンツを取得できます。
seo-title: Android でのオファーコンテンツのプリフェッチ
title: Android でのオファーコンテンツのプリフェッチ
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Android でのオファーコンテンツのプリフェッチ {#prefetch-offer-content-in-android}

Adobe Target のプリフェッチ機能では、サーバーからの応答をキャッシュすることで、Android Mobile SDK を使用して可能な限り少ない回数でオファーコンテンツを取得できます。

>[!IMPORTANT]
>
>Android用のモバイルSDKのプリフェッチ機能は、Adobe targetの自動ターゲット、自動配分、自動パーソナライゼーションアクティビティタイプではサポートされていません。

このプロセスにより、読み込み時間が短縮され、複数のネットワーク呼び出しが回避されるほか、モバイルアプリユーザーがどの mbox を訪問したかを Adobe Target に通知することができます。プリフェッチ呼び出し中にすべてのコンテンツが取得され、キャッシュされます。このコンテンツは、指定された mbox 名のキャッシュされたコンテンツを含む今後のすべての呼び出しに対してキャッシュから取得されます。

プリフェッチコンテンツは、起動間で保持されません。The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

SDK バージョン 4.14 以降で、`environmentId``ADBMobileConfig.json` が指定されている場合、v2 バッチ mbox TnT 呼び出しを開始すると、 ファイルから environmentId を取得します。このファイルで `environmentId` が指定されていない場合、TNT バッチ mbox 呼び出しで環境パラメーターは送信されず、オファーはデフォルト環境に配信されます。

以下に例を示します。

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

以下に、Android でのプリフェッチで使用できるメソッドを示します。

* **prefetchContent**

   設定されている Target サーバーに、ロケーションの配列と共にプリフェッチの要求を送信し、指定されたコールバックで要求ステータスを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * このメソッドのパラメーターを次に示します。

      * **targetPrefetchArray**

         プリフェッチする各 Target のロケーションの名前と mboxParameters を含む `TargetPrefetchObjects` の配列。

      * **profileParameters**

         この要求のすべてのロケーションプリフェッチで使用されるプロファイルパラメーターのキーと値が含まれます。

      * **callback**

         プリフェッチの完了時に呼び出されます。Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   リクエスト配列に指定された複数の mbox の場所に対してバッチリクエストを実行します。配列内の各オブジェクトにコールバック関数が含まれ、指定された mbox のロケーションに対してコンテンツが使用可能になると呼び出されます。

   >[!IMPORTANT]
   >
   >要求された場所のコンテンツが既にキャッシュされている場合、指定されたコールバックで直ちに返されます。 コンテンツがキャッシュされていない場合は、SDK は Target サーバーにネットワーク要求を送信してコンテンツを取得します。

   * このメソッドの構文を次に示します。

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * このメソッドのパラメーターを次に示します。

      * **requestArray**

         取得するロケーションごとに、名前、デフォルトコンテンツ、パラメーターおよびコールバック関数を含む `TargetRequestObjects` の配列。

      * **profileParameters**

         このリクエストのすべての場所でのプリフェッチで使用するプロファイルパラメーターのキーと値を含みます。

* **clearPrefetchCache**

   Target プリフェッチによってキャッシュされたデータをクリアします。

   * このメソッドの構文を次に示します。

      ```java
      public static void clearPrefetchCache();
      ```

   * このメソッドにはパラメーターがありません。

* **createTargetRequestObject**

   指定されたデータを使用して `TargetRequestObject` のインスタンスを作成し、返します。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   指定されたデータを使用して TargetPrefetchObject のインスタンスを作成し、返します。

   * このメソッドの構文を次に示します。

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

以下に、Android でのプリフェッチをサポートするパブリッククラスを示します。

### クラス参照：TargetPrefetchObject

mbox 名と、mbox のプリフェッチで使用されるパラメーターをカプセル化します。

* **`name`**

   プリフェッチするロケーションの名前。
   * **型**：String

* `mboxParameters`

   この `mboxParameters` の要求の `TargetPrefetchObject` として添付されるキー値のペアのコレクション。
   * **タイプ**:マップ`<String, Object>`

* **`orderParameters`**

   order ノード下の現在の mbox に添付されるキー値のペアのコレクション。
   * **タイプ**:マップ `<String, Object>`

* **`productParameters`**

   product ノード下の現在の mbox に添付されるキー値のペアのコレクション。

   * **タイプ**:マップ `<String, Object>`


### クラス参照：TargetRequestObject

このクラスは、mbox 名、デフォルトコンテンツ、mbox パラメーターおよび Target ロケーションの要求に使用されるリターンコールバックをカプセル化します。

* **`mboxName`**

   要求されるロケーションの名前。

   * **型**：String

* **`mboxParameters`**

   この `mboxParameters` の `TargetRequestObject` として添付されるキー値のペアのコレクション。

   * **タイプ：マップ`<String, Object>`**

* **`orderParameters`**

   order ノード下の現在の mbox に添付されるキー値のペアのコレクション。

   * **タイプ**:マップ `<String, Object>`

* **`productParameters`**

   product ノード下の現在の mbox に添付されるキー値のペアのコレクション。

   * **タイプ**:マップ `<String, Object>`

* **`defaultContent`**

   SDK が Target サーバーからコンテンツを取得できない場合にコールバックで返される文字列値。

   * **型**：String

* **`callback`**

   指定された `TargetRequestObject` のコンテンツが使用可能な場合に呼び出される関数ポインター。

   * **タイプ**:Target.TargetCallback`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

以下に、Android SDK を使用してコンテンツをプリフェッチする方法の例を示します。

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
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

* `purchasedProducts` は、文字列の ArrayList を受け付けます。
