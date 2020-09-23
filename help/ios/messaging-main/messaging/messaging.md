---
description: この情報は、iOSアプリでアプリ内メッセージを使用する際に役立ちます。
seo-description: この情報は、iOSアプリでアプリ内メッセージを使用する際に役立ちます。
seo-title: アプリ内メッセージ
solution: Experience Cloud,Analytics
title: アプリ内メッセージ
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 55%

---


# アプリ内メッセージ {#in-app-messaging}

この情報は、iOSアプリでアプリ内メッセージを使用する際に役立ちます。

To use in-app messaging, you **must** have SDK version 4.2 or later.

注意事項：

* メッセージおよびメッセージを表示するタイミングを定義するルールは、AdobeのMobile Servicesで作成されます。 For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* この節で説明する更新は、アプリ内メッセージを表示するために、SDKに対して行う必要があります。

   >[!TIP]
   >
   >メッセージを定義していない場合でも、これらの手順を実行できます。定義したメッセージは、アプリに動的に配信され、アプリストアの更新なしで表示されます。

## アプリ内メッセージの有効化 {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/requirements.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. アプリ内メッセージに必要な設定が `ADBMobileConfig.json` ファイルに含まれていることを確認します。
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
   >`messages` または `remotes` が必要です。

   これらのオブジェクトが設定されていない場合は、更新された `ADBMobileConfig.json` ファイルを Adobe Mobile Services からダウンロードしてください。詳しくは、「[コア実装とライフサイクルい](/help/ios/getting-started/requirements.md)」を参照してくださ。

## アプリ内メッセージの追跡 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

iOS Mobile Services SDKは、アプリ内メッセージに関する以下の指標を追跡します。

* アプリ内メッセージのフルスクリーンおよび警告スタイルの場合：

   * **[!UICONTROL インプレッション]**：ユーザーがアプリ内メッセージをトリガーしたとき。
   * **[!UICONTROL クリックスルー]**：ユーザーが&#x200B;**[!UICONTROL クリックスルー]**&#x200B;ボタンを押したとき。
   * **[!UICONTROL キャンセル]**：ユーザーが&#x200B;**[!UICONTROL キャンセル]**&#x200B;ボタンを押したとき。

* カスタムの全画面アプリ内メッセージの場合は、メッセージ内の HTML コンテンツに次のボタンに関する SDK 追跡を通知する正しいコードが含まれている必要があります。

   * **[!UICONTROL クリックスルー]**（リダイレクト）のトラッキング例： `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL キャンセル]**（終了）追跡の例：`adbinapp://cancel`

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

## ローカルフォールバック画像 {#section_DEACC1CE549B4573B556A44A52409941}

AdobeのMobileサービスでフルスクリーンメッセージを作成する場合、オプションでフォールバック画像を指定できます。 メッセージがWebから目的の画像を取得できない場合、SDKは、アプリケーションバンドルから同じ名前の画像を読み込もうとします。 これにより、ユーザーがオフラインの場合や、事前に決められている画像が未到達の場合でも、メッセージを元の形式で表示できます。

フォールバックAdobeのアセット名は、Mobile Servicesでメッセージを設定する際に指定します。

>[!IMPORTANT]
>
>指定したリソースが使用可能であることを確認する必要があります。

