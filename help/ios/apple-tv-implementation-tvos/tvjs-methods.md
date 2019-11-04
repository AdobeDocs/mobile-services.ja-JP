---
description: tvOS ライブラリが提供する TVJS メソッドの一覧を以下に示します。
seo-description: tvOS ライブラリが提供する TVJS メソッドの一覧を以下に示します。
seo-title: TVJS メソッド
solution: Experience Cloud,Analytics
title: TVJS メソッド
topic: 開発者と導入
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS メソッド {#tvjs-methods}

tvOS ライブラリが提供する TVJS メソッドの一覧を以下に示します。

## 設定メソッド{#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Adobe Mobile ライブラリの現在のバージョンを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      version()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * 戻り値：`String`

* **privacyStatus**

   現在のユーザーのプライバシーステータスの enum の NSUInteger 表現を返します。

   以下のオプションがあります。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットが破棄されます。
   * `ADBMobilePrivacyStatusUnknown`：オフライン追跡が有効である場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      privacyStatus()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * 戻り値：`Number`

* **setPrivacyStatus**

   現在のユーザーのプライバシーステータスを以下の値のいずれかに設定します。

   * `ADBMobilePrivacyStatusOptIn`：ヒットは即座に送信されます。
   * `ADBMobilePrivacyStatusOptOut`：ヒットが破棄されます。
   * `ADBMobilePrivacyStatusUnknown`：オフライン追跡が有効である場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。
   オフライン追跡が有効になっていない場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   現在のユーザーのライフタイム値を返します。デフォルト値は `0` です。

   * このメソッドの構文を次に示します。

      ```objective-c
      lifetimeValue()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * 戻り値：`Number`

* **userIdentifier**

   カスタム識別子が設定されている場合は、ユーザー識別子を返します。カスタム識別子が設定されていない場合は、nil を返します。デフォルトは `nil` です。

   >[!IMPORTANT]
   >
   >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前のカスタムまたは自動生成された訪問者 ID が取得され、カスタムユーザー識別子として保存されます。これによって、SDK をアップグレードしても訪問者データが保持されます。4.x SDK を新規インストールした場合は、ユーザー識別子は設定されるまで nil となります。

   * このメソッドの構文を次に示します。

      ```objective-c
      userIdentifier()
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * 戻り値：`String`

* **setUserIdentifier**

   ユーザー識別子を設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      setUserIdentifier(userId)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * 戻り値：なし

   * パラメーター：`userID`

      * 型：String
      * このユーザーの新しい識別子。

* **setAdvertisingIdentifier**

   SDK で IDFA を設定します。既に SDK に設定されている場合は、IDFA をライフサイクルで送信します。IDFA にはシグナル（ポストバック）でもアクセスできます。

   >[!IMPORTANT]
   >
   >広告サービスを使用している場合にのみ、Apple API から IDFA を取得してください。IDFA を取得し、正しく使用していない場合は、アプリが拒否されることがあります。

   * このメソッドの構文を次に示します。

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * 戻り値：なし
   * パラメーター：`idfa`
      * 型：`String`
      * Apple API から取得した IDFA。

* **setDebugLogging**

   デバッグログの環境設定をします。

   * このメソッドの構文を次に示します。

      ```objective-c
      setDebugLogging(logging)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * 戻り値：なし
   * パラメーター：`logging`
      * 型：`Bool`
      * Adobe SDK がデバッグコンソールをログ記録するかどうかを指示する値。


## Analytics メソッド{#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、アプリで使用可能なビューのことで、home dashboard、app settings、cart などがあります。これらの状態は Web サイト上のページによく似ており、trackState コールはページビュー数を増分します。

   状態が空の場合、レポートに「app name app version (build)」と表示されます。レポートにこの値が表示される場合、各 trackState コールで状態を設定していることを確認してください。

   >[!TIP]
   >
   >これは、ページビュー数を増分する唯一のトラッキングコールです。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * 戻り値：なし
      * パラメーター：`stateName`
         * 型：`String`
         * ページの状態名。
      * パラメーター：`contextData`
         * 型：Object
         * このヒットの追加コンテキストデータ。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   アプリのアクションを追跡します。アクションとは、アプリ内で計測に価する重要な操作のことで、logons、banner taps、feed subscriptions などの指標があります。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * 戻り値：なし
      * パラメーター：`actionName`
         * 型：String
         * 追跡するアクション名。
      * パラメーター：`contextData`
         * 型：Object
         * このヒットの追加コンテキストデータ。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   現在地点の緯度と経度の座標を送信します。

   また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点（POI）内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` コールで送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * 戻り値：なし
      * パラメーター：`lat`
         * 型：Number
         * 現在位置の緯度。
      * パラメーター：`lon`
         * 型：Number
         * 現在位置の経度。
      * パラメーター：`contextData`
         * 型：Object
         * このヒットの追加コンテキストデータ。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   ユーザーのライフタイム値に値を加算します。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * 戻り値：なし
      * パラメーター：`increaseAmount`
         * 型：Number
         * ユーザーの現在のライフタイム値に追加する値。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   指定アクションの時間計測を開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * 戻り値：なし
      * パラメーター：`name`
         * 型：String
         * 追跡する時間計測アクション名。
      * パラメーター：`contextData`
         * 型：Object
         * このヒットの追加コンテキストデータ。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   特定のアクションに関連付けられたコンテキストデータを指定データで更新します。

   指定データがそのアクションの既存データに追加され、アクションに対して同じキーが既に定義されている場合は、データを上書きします。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * 戻り値：なし
      * パラメーター：`name`
         * 型：String
         * 更新する時間計測アクション名。
      * パラメーター：`contextData`
         * 型：Object
         * このヒットの追加コンテキストデータ。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   時間計測アクションを終了します。

   コールバック関数を指定した場合、最終時刻値にアクセスできます。コールバックを指定しない場合またはコールバックが true を返した場合、Adobe SDK が自動的にヒットを送信します。コールバックが false を返した場合、時間計測アクションのヒットは送信されません。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * 戻り値：なし
      * パラメーター：`name`
         * 型：String
         * 終了する時間計測アクション名。
      * パラメーター：`callback`
         * 型：`function(inAppDuration, totalDuration, data)`
         * パラメーターとして `inAppDuration`（数値）、`totalDuration`（数値）、`data`（コンテキストデータオブジェクト）を持つコールバックメソッド。

            コールバック関数で `false` を返すことによって、SDK が最終ヒットを送信しないようにすることができます。
      * このメソッドのコードサンプルを次に示します。

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   時間計測アクションが進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * 戻り値：Bool
      * パラメーター：`name`
         * 型：`String`
         * 存在を確認する必要がある時間指定アクションの名前。
   * このメソッドのコードサンプルを次に示します。


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   自動的に生成された訪問者識別子を返します。

   これは、アドビのサーバーによって生成される、アプリ固有の一意の訪問者 ID です。生成時にアドビのサーバーに到達できない場合、ID は Apple の CFUUID を使用して生成されます。値は初期起動時に生成され、保存されて、その時点から使用されます。この ID はアプリをアップグレードしても保持され、標準的なアプリケーションバックアッププロセス中に保存および復元され、アプリをアンインストールすると削除されます。

   >[!TIP]
   >
   >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前のカスタムまたは自動生成された訪問者 ID が取得され、カスタムユーザー識別子として保存されます。これによって、SDK をアップグレードしても訪問者データが保持されます。4.x SDK を新規インストールした場合、ユーザー識別子は `nil` なので、トラッキング識別子が使用されます。詳しくは、以下の userIdentifier 行を参照してください。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackingIdentifier()
      ```

      * 戻り値：`String`
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   現在キューに格納されている件数にかかわらず、オフラインキューのすべてのヒットを強制的に送信します。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackingSendQueuedHits()
      ```

      * 戻り値：なし
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   オフラインキューからすべてのヒットをクリアします。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackingClearQueue()
      ```

      * 戻り値：なし
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   現在オフラインキュー内に格納されているヒットの数を取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      trackingGetQueueSize()
      ```

      * 戻り値：Number
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager メソッド{#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   取得された最も直近の訪問者プロファイルを返します。

   まだシグナルが送信されていない場合は null を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`NSUserDefaults` に保存されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      audienceVisitorProfile()
      ```

      * 戻り値：Object
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   現在の DPID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      audienceDpid()
      ```

      * 戻り値：String
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   現在の DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      audienceDpuuid()
      ```

      * 戻り値：`String`
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   dpid と dpuuid を設定します。設定されている場合は、それぞれのシグナルとともに送信されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * 戻り値：なし
      * パラメーター：`dpid`
         * 型：`String`
         * Audience Manager のデータプロバイダー ID。
      * パラメーター：`dpuuid`
         * 型：`String`
         * ユーザーとデータプロバイダーの組み合わせに対する識別子。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Audience Manager に特性とともにシグナルを送信し、コールバック関数で返された一致セグメントを取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * パラメーター：`traits`
         * 型：Object
         * このユーザーの特性辞書。
      * パラメーター：`callback`
         * 型：function(profile)
         * コールバック関数のパラメーターに Audience Manager から返されたプロファイル。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Audience Manager UUID をリセットし、現在の訪問者プロファイルを削除します。

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      audienceReset()
      ```

      * 戻り値：なし
      * パラメータ：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID サービスメソッド {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Experience Cloud ID を ID サービスから取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      visitorMarketingCloudID()
      ```

      * 戻り値：String
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Experience Cloud ID に加え、各訪問者に関連付ける追加の顧客 ID を設定できます。訪問者 API は、同じ訪問者に対して複数の顧客 ID と、異なる顧客 ID の範囲を区別するための顧客タイプ識別子を受け取ります。このメソッドは、JavaScript ライブラリの setCustomerIDs に相当します。

   * このメソッドの構文を次に示します。

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * 戻り値：なし
      * パラメーター：`identifiers`

         * 型：`Object`
         * このユーザーの ID サービスに同期する識別子。
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   指定された識別子を ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * 戻り値：なし
      * パラメーター：`identifiers`
         * 型：`Object`
         * このユーザーの ID サービスに同期する識別子。
      * パラメーター：`authState`
         * 型：ADBMobileVisitorAuthenticationState
         * ユーザーの認証状態。次の値を指定できます。
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   指定された識別子の型と値を ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * 戻り値：なし
      * パラメーター：`idType`
         * 型：`String`
         * 同期する識別子の型。
      * パラメーター：`identifier`
         * 型：`String`
         * 同期する識別子の値。
      * パラメーター：`authState`
         * 型：ADBMobileVisitorAuthenticationState
ユーザーの認証状態。指定できる値には以下のものがあります。
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   読み取り専用の ADBVisitorID オブジェクトの配列を取得します。以下のコードサンプルは、VisitorID オブジェクトの一例です。

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * このメソッドの構文を次に示します。

      ```objective-c
      visitorGetIDsJs()
      ```

      * 戻り値：`Array [Object]`

      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target メソッド {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   サードパーティの ID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      targetThirdPartyID()
      ```

      * 戻り値：`String`
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   サードパーティの ID を設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * 戻り値：なし
      * パラメーター：`thirdPartyID`
         * 型：`String`
         * Target リクエストに使用するサードパーティ ID。
   * このメソッドのコードサンプルを次に示します。
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   PcID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      targetPcID()
      ```

      * 戻り値：`String`
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   セッション ID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      targetSessionID()
      ```

      * 戻り値：`String`
      * パラメーター：なし
   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
