---
description: iOS PhoneGap プラグインメソッドを使用して、様々なタスクを完了できます。
keywords: android;library;mobile;sdk
seo-description: iOS PhoneGap プラグインメソッドを使用して、様々なタスクを完了できます。
seo-title: PhoneGapプラグインのメソッド
solution: Marketing Cloud、Analytics
title: PhoneGapプラグインのメソッド
topic: 開発者と導入
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Android PhoneGap プラグインのメソッドを使用して、様々な作業を実行できます。

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   現在のユーザーのプライバシーステータスを返します。

   利用可能なステータスは次のとおりです。

   * `ADB.optedIn`:ヒットはすぐに送信されます。
   * `ADB.optedOut`:ヒットは破棄されます。
   * `ADB.optUnknown`:レポートスイート **で** タイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。レポートスイートのタイムスタンプが&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

      デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   現在のユーザーのプライバシーステータスを `status` に設定します。

   次のいずれかのステータスを設定できます。

   * `ADB.optedIn`:ヒットはすぐに送信されます。
   * `ADB.optedOut`:ヒットは破棄されます。
   * `ADB.optUnknown`:レポートスイート **で** タイムスタンプが有効になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。レポートスイートのタイムスタンプが&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   現在のユーザーのライフタイム値を返します。デフォルト値は 0 です。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. デフォルトでは、この変数は `false` です。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   ライブラリのバージョンを取得します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   自動的に生成された訪問者識別子を返します。

   これは、アプリの初回起動時に生成され、それ以降、保存および使用されるアプリ固有の一意の訪問者 ID です。この ID は、アプリをアップグレードしても保持され、アプリをアンインストールすると削除されます。

   >[!TIP]
   >
   >アプリケーションがExperience Cloud3. x SDKから4. x SDKにアップグレードすると、以前の訪問者ID（カスタムまたは自動生成）が取得され、カスタムユーザー識別子として保存されます。詳しくは、以下を `getUserIdentifier` 参照してください。SDK をアップグレードしても、この ID の訪問者データは保持されます。

   4.x SDK を新規インストールした場合、ユーザー識別子は `null` なので、トラッキング識別子が使用されます。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   顧客ユーザー識別子が設定されている場合は、その識別子を返します。顧客ユーザー識別子が設定されていない場合は、`null` を返します。デフォルト値は `null` です。

   * このメソッドのコードサンプルを次に示します。

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   プッシュ通知用のデバイストークンを設定します。

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * このメソッドの構文を次に示します。

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   ライフサイクルセッションのキープアライブの設定をおこないます。

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. このメソッドは、アプリがバックグラウンドで通知を登録する場合にのみ使用してください。

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   現在のバッチオプションに関係なく、キュー内に格納されているすべてのヒットを強制的に送信します。

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   オフラインキュー内に格納されているトラッキングコールの数を取得または設定します。

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   オフラインキュー内に格納されているすべてのトラッキングコールを削除します。

   >[!WARNING]
   >
   >キューを手動でクリアする場合は、元に戻すことができません。これは、元に戻すことができないからです。

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   PII 収集リクエストを送信します。

   * このメソッドの構文を次に示します。
   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   アドビディープリンクのクリックスルーを追跡します。

   >[!TIP]
   >
   >ライフサイクル呼び出しが起動イベントの場合、Adobeリンクデータは追加されます。それ以外の場合は、追加の呼び出しが送信されます。

   * このメソッドの構文を次に示します。

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。

   `cData`：コンテキストデータで送信されるキーと値のペアを持つ JSON オブジェクト。

   * このメソッドの構文を次に示します。

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   アプリのアクションを追跡します。Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * このメソッドの構文を次に示します。

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   現在の XY 座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   `action` という名前の時間計測アクションを開始します。

   既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   渡された `cData` は、アクションの既存のデータに追加されます。`action` に対して同じキーが既に定義されている場合は、データが上書きされます。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   時間計測アクションを終了します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   時間計測アクションが進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   ユーザーがいつビーコンの Proximity に入ったかを追跡します。

   * このメソッドの構文を次に示します。

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   ユーザーがビーコンの Proximity を離れた場合に、ビーコンデータをクリアします。

   * このメソッドの構文を次に示します。

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Target メソッド {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   設定した `Target` サーバーにリクエストを送信し、オファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   設定した `Target` サーバーにリクエストを送信します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   共有 Cookie ストレージから `Target` の Cookie をクリアします。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   `Target` サービスリクエストを処理します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   `Target` サービスリクエストを処理します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Target サーバーによってこの訪問者に対して返された `SessionID` Cookie の値を取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   `PcID` サーバーによってこの訪問者に対して返された `Target` Cookie の値を取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Target のカスタム訪問者 ID を設定します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Target のカスタム訪問者 ID を取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   設定した Target サーバーにリクエストを送信し、オファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. 詳しくは [、設定メソッド](/help/android/configuration/methods.md)を参照してください。

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   訪問者のプロファイルを取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   DPID を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   DPID および DPUUID を設定します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Audience Manager サービスリクエストを処理します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUIDを使用して、現在の訪問者プロファイルを削除します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   ID サービスから Experience Cloud ID を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   指定された識別子を ID サービスと同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   指定された識別子を ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   指定された識別子を ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   指定された URL に訪問者識別子を追加します。

   * このメソッドの構文を次に示します。

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```