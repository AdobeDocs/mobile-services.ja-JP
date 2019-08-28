---
description: iOS アプリでアプリ内メッセージを使用するのに役立つ情報です。
seo-description: iOS アプリでアプリ内メッセージを使用するのに役立つ情報です。
seo-title: アプリ内メッセージ
solution: Marketing Cloud、Analytics
title: アプリ内メッセージ
topic: 開発者と導入
uuid: 21fa6a94- bb7f-4c78-843b- a50f1974db22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# アプリ内メッセージ {#in-app-messaging}

iOS アプリでアプリ内メッセージを使用するのに役立つ情報です。

アプリ内メッセージを使用するには、SDK バージョン 4.2 以降が&#x200B;**必要**&#x200B;です。

注意事項：

* メッセージおよびメッセージをいつ表示するかを定義するルールは、Adobe Mobile Services で作成されます。詳しくは、[アプリ内メッセージの作成](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)を参照してください。
* アプリ内メッセージを表示するには、この節で説明するアップデートを SDK に対しておこなう必要があります。

   >[!TIP]
   >
   >メッセージが定義されていない場合でも、これらの手順を完了できます。メッセージを定義すると、アプリに動的に配信され、アプリストアの更新なしで表示されます。

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/requirements.md)してください。

1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `ADBMobileConfig.json` アプリ内メッセージに必要な設定がファイルに含まれていることを確認します。
1. アプリ内メッセージを起動時に動的に更新するには、`remotes` オブジェクトが存在し、正しく設定されている必要があります。

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` または `remotes` 必須です。

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 詳しくは、 [コアの実装とライフサイクル](/help/ios/getting-started/requirements.md)を参照してください。

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile Services SDK はアプリ内メッセージに関する次の指標を追跡します。

* 全画面および警告方式のアプリ内メッセージの場合：

   * **[!UICONTROL インプレッション]**&#x200B;数:ユーザーがアプリ内メッセージをトリガーしたとき。
   * **[!UICONTROL クリックスルー]**:ユーザが **[!UICONTROL クリックスルー]** ボタンを押したとき。
   * **[!UICONTROL キャンセル]**:ユーザーが **[!UICONTROL 「キャンセル」]** ボタンを押すと、

* カスタムの全画面アプリ内メッセージの場合は、メッセージ内の HTML コンテンツに次のボタンに関する SDK 追跡を通知する正しいコードが含まれている必要があります。

   * **[!UICONTROL クリックスルー]** （リダイレクト）の例: `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL キャンセル]** （閉じる）の例: `adbinapp://cancel`

* ローカル（リモート）通知の場合：

   * **[!UICONTROL インプレッション]**：ユーザーが通知をトリガーしたとき。
   * **[!UICONTROL オープン]**：ユーザーが通知からアプリケーションを開いたとき。
   以下にオープン追跡のコードを追加した例を示します。

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Adobe Mobile Services で全画面表示メッセージを作成する際、オプションでフォールバック画像を指定できます。メッセージが Web から目的の画像を取得できない場合、SDK はアプリケーションバンドルから同じ名前の画像を読み込もうとします。この機能により、ユーザーがオフラインだったり、既定の画像に到達できなくても、オリジナルの形でメッセージを表示できます。

フォールバック画像のアセット名は、Adobe Mobile Services でメッセージを設定する際に指定します。

>[!IMPORTANT]
>
>指定したリソースを使用できるようにする必要があります。

