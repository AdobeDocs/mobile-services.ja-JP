---
description: iOS PhoneGap プラグインメソッドを使用して、様々なタスクを完了できます。
keywords: phonegap
seo-description: iOS PhoneGap プラグインメソッドを使用して、様々なタスクを完了できます。
seo-title: PhoneGap プラグインのメソッド
solution: Marketing Cloud,Analytics
title: PhoneGap プラグインのメソッド
topic: Developer and implementation
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '1730'
ht-degree: 100%

---


# PhoneGap プラグインのメソッド {#phonegap-plug-in-methods}

iOS PhoneGap プラグインメソッドを使用して、様々なタスクを完了できます。

トラッキングを使用する `html` ファイル内で、以下を `<head>` タグに追加します。

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## 設定メソッド {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   現在のユーザーのプライバシーステータスを返します。利用可能なステータスは次のとおりです。

   * `ADB.optedIn`：ヒットは即座に送信されます。
   * `ADB.optedOut`：ヒットは破棄されます。
   * `ADB.optUnknown`レポートスイートのタイムスタンプが有効に&#x200B;**なっている**&#x200B;場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。レポートスイートのタイムスタンプが&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。\
      デフォルト値は `ADBMobileConfig.json` ファイルに設定します。

      * このメソッドのコードサンプルを次に示します。

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   現在のユーザーのプライバシーステータスを `status` に設定します。次のいずれかのステータスを設定できます。
   * `ADB.optedIn`：ヒットは即座に送信されます。
   * `ADB.optedOut`：ヒットは破棄されます。
   * `ADB.optUnknown`：レポートスイートのタイムスタンプが&#x200B;**有効になっている**&#x200B;場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      レポートスイートのタイムスタンプが&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   現在のユーザーのライフタイム値を返します。デフォルト値は 0 です。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   デバッグ情報を表示する設定を、有効（`true`）または無効（`false`）にします。デフォルトでは、この変数は `false` です。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   ライブラリのバージョンを取得します。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   自動的に生成された訪問者識別子を返します。これは、アプリが最初に起動されたときに生成され、その時点から保存されて使用される、アプリ固有の一意の訪問者 ID です。この ID は、アプリがアップグレードされても保持され、アプリがアンインストールされると削除されます。

   >[!TIP]
   >
   >アプリを Experience Cloud 3.x から 4.x SDK にアップグレードした場合、以前の訪問者 ID（カスタムまたは自動生成）が取得され、カスタムユーザー識別子として保存されます（以下の `getUserIdentifier` 行を参照してください）。これにより、SDK をアップグレードしても訪問者データは保存されます。4.x SDK を新規インストールした場合、ユーザー識別子は `null` なので、トラッキング識別子が使用されます。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   カスタム識別子が設定されている場合は、カスタムユーザー識別子を返します。カスタム識別子が設定されていない場合は、`null` を返します。デフォルト値は `null` です。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   ユーザー識別子を `identifier` に設定します。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   プッシュ通知用のデバイストークンを設定します。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   ライフサイクルセッションのキープアライブの設定をおこないます。

   >[!IMPORTANT]
   >
   >`keepLifecycleSessionAlive` を呼び出すと、アプリを次回バックグラウンドから再開するときに新しいセッションを開始できなくなります。このメソッドは、アプリがバックグラウンドで通知を登録する場合にのみ使用してください。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   現在のバッチオプションに関係なく、キュー内に格納されているすべてのヒットを強制的に送信します。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   オフラインキュー内に格納されているトラッキングコールの数を取得または設定します。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   オフラインキュー内に格納されているすべてのトラッキングコールを削除します。

   >[!CAUTION]
   >
   >キューを手動でクリアする場合は、慎重に実行してください。この操作を元に戻すことはできません。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   設定ファイル内のライフサイクルセッションのタイムアウト値にかかわらず、バックグラウンドから次に戻ったときに新しいセッションを開始しないように SDK に指示します。

   >[!IMPORTANT]
   >
   >重要：このメソッドは、バックグラウンドにある間に通知を登録するアプリで使用されることを目的としており、アプリがバックグラウンドにある間に実行されるコードからのみ呼び出される必要があります。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   SDK のすべてのソリューションで使用するライフサイクルデータを収集するように SDK に指示します。詳しくは、「[ライフサイクル指標](/help/ios/metrics.md)」を参照してください。

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII メソッド {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   PII 収集リクエストを送信します。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## トラッキングメソッド {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   アドビディープリンクのクリックスルーを追跡します。

   >[!TIP]
   >
   >ライフサイクル呼び出しが起動イベントの場合は、アドビリンクデータが追加されます。それ以外の場合は、追加の呼び出しが送信されます。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   プッシュメッセージのクリックスルーを追跡します。

   * このメソッドの構文を次に示します。

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   ローカルな通知メッセージのクリックスルーを追跡します。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   オプションのコンテキストデータを使用してアプリの状態を追跡します。状態とは、アプリで使用可能なビューのことで、`home dashboard`、`app settings`、`cart` などがあります。これらの状態は Web サイト上のページによく似ており、`trackState` コールはページビュー数を増分します。cData は、コンテキストデータで送信されるキーと値のペアを持つ JSON オブジェクトです。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   アプリのアクションを追跡します。アクションとは、アプリ内で計測に価する重要な操作のことで、`feed subscriptions`、`logins`、`banner taps` などの指標があります。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   バックグラウンドで発生したアクションを追跡します。これにより、特定のシナリオでライフサイクルイベントが発生しないようにします。

   * このメソッドの構文を次に示します。

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   現在の X 座標と Y 座標を送信します。また、現在位置が `ADBMobileConfig.json` ファイルで定義された目標地点内にあるかどうかを判定します。現在の座標が定義した目標地点内にある場合、コンテキストデータ変数に代入され、`trackLocation` 呼び出しで送信されます。

   * このメソッドの構文を次に示します。

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   ユーザーのライフタイム値に `amount` を加算します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   `action` という名前の時間計測アクションを開始します。既に開始しているアクションでこのメソッドを呼び出すと、以前の時間計測アクションが上書きされます。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   `cData` を渡して、特定の `action` に関連付けられているコンテキストデータを更新します。渡された `cData` は、特定のアクションの既存のデータに追加され、同じキーが既に `action` に定義されている場合は、データを上書きします。

   >[!TIP]
   >
   >この呼び出しはヒットを送信しません。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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

   時間計測が進行中かどうかを返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Target メソッド {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   設定した `Target` サーバーにリクエストを送信し、オファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   設定した Target サーバーにリクエストを送信します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   共有 Cookie ストレージから Target の Cookie をクリアします。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Target サービスリクエストを処理します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Target サービスリクエストを処理します。

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
      ADB.targetSessionID(success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Target サーバーによってこの訪問者に対して返された `PcID` Cookie の値を取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetPcID(success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Target のカスタム訪問者 ID を設定します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * このグループのコードサンプルを次に示します。

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Target のカスタム訪問者 ID を取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## 獲得メソッド {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   開発者は、ユーザーがダウンロード計測用リンクをクリックしていない場合でも、クリックした場合と同じようにアプリ獲得キャンペーンを開始できます。手動でのダウンロード計測用リンクの作成や、（`SKStoreView` と同様に）App Store リダイレクトの処理に役立ちます。

   * このメソッドの構文を次に示します。

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## 広告識別子 {#section_194607D101B047A19C51B19E176E1500}

Cordova が生成した `AppDelegate` では、`application:didFinishLaunchingWithOptions:` delegate メソッド内で `[ADBMobile setAdvertisingIdentifier:]` を呼び出します。詳しくは、「[設定メソッド](/help/ios/configuration/sdk-methods.md)」を参照してください。

## Audience Manager メソッド {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   訪問者のプロファイルを取得します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   DPID を返します。

   * このメソッドの構文を次に示します。

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   DPID および DPUUID を設定します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Audience Manager サービスリクエストを処理します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID をリセットし、現在の訪問者プロファイルを削除します。

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.audienceReset(); 
      ```

## ID サービスメソッド {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   ID サービスから Experience Cloud ID を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   指定された識別子を ID サービスと同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   指定された識別子を訪問者 ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   指定された識別子を訪問者 ID サービスに同期します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   指定された URL に訪問者識別子を追加します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   同期されたすべての `visitorIDs` を返します。

   * このメソッドの構文を次に示します。

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

