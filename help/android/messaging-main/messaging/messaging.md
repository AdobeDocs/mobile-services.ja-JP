---
description: 分析データまたはイベントからトリガーされるアプリ内メッセージを配信できます。実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。
seo-description: 分析データまたはイベントからトリガーされるアプリ内メッセージを配信できます。実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。
seo-title: アプリ内メッセージ
solution: Marketing Cloud,Analytics
title: アプリ内メッセージ
topic: 開発者と導入
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# アプリ内メッセージ {#in-app-messaging}

分析データまたはイベントからトリガーされるアプリ内メッセージを配信できます。実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

>[!IMPORTANT]
>
>2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、[Launch](https://launch.adobe.com/) にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>アプリ内メッセージを使用するには、SDK バージョン 4.2 以降が&#x200B;**必要**&#x200B;です。

メッセージと、メッセージが表示されるタイミングを定義するルールを Adobe Mobile Services で作成できます。詳しくは、[アプリ内メッセージの作成](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)を参照してください。アプリ内メッセージを表示するには、SDK を更新する必要があります。メッセージを定義していない場合でも、これらの手順を実行することができます。定義したメッセージは、アプリに動的に配信され、アプリストアの更新なしで表示されます。

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、 *Core実装およびライフサイクルのIntelliJ IDEAまたはEclipse ProjectへのSDKと設定ファイルの追加*[を参照してください](/help/android/getting-started/dev-qs.md)。

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   モーダルレイアウトを選択した場合は、メッセージに対して次のいずれかのテーマを選択します。

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   以下に例を示します。

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. それぞれの `collectLifecycleData` 呼び出しで、`this` を渡して現在のアクティビティへの参照を指定します。

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` または `remotes` が必要です。

   起動時にアプリ内メッセージを動的に更新するには、`remotes` オブジェクトが存在し、正しく設定されている必要があります。

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

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. 詳しくは、[開始する前に](/help/android/getting-started/requirements.md)を参照してください。

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Android Mobile SDK はアプリ内メッセージに関する次の指標を追跡します。

* 全画面および警告方式のアプリ内メッセージの場合：

   * **インプレッション**：ユーザーがアプリ内メッセージをトリガーしたとき。
   * **Click throughs: when user presses Click through.******
   * **キャンセル**:ユーザーが「キャンセル」を **[!UICONTROL 押したとき]**。

* カスタムの全画面アプリ内メッセージの場合は、メッセージ内の HTML コンテンツに次のボタンに関する SDK 追跡を通知する正しいコードが含まれている必要があります。

   * **クリックスルー** （リダイレクト）のトラッキング例：

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Cancel** (close)サンプルトラッキング：

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

フルスクリーンメッセージを作成する場合は、オプションでフォールバック画像を指定できます。メッセージで Web から目的の画像を取得できない場合、SDK はアプリケーションの assets フォルダーから同じ名前の画像をロードしようとします。これにより、ユーザーがオフライン状態の場合や、事前設定された画像に到達できない場合でも、元の形式でメッセージを表示することができます。

>[!IMPORTANT]
>
>フォールバック画像アセット名は、Adobe Mobile Servicesでメッセージを設定する際に指定します。また、指定したリソースが使用可能であることを確認する必要があります。

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

次のメソッドを使用すると、通知領域に表示される小さいアイコンと大きいアイコンのほか、通知ドロワーに通知が表示されたときに表示される大きいアイコンを設定できます。

* **Config.setSmallIconResourceId(int resourceId)**

   SDK で作成される通知に使用される小さいアイコンを設定します。このアイコンは、ステータスバーに表示されます。ユーザーが通知センターで完全な通知を表示する際に表示されるセカンダリ画像です。

   * このメソッドの構文を次に示します。

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * このメソッドのコード例を次に示します。

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   SDK で作成される通知に使用される大きいアイコンを設定します。このアイコンは、ユーザーが通知センターで通知を完了したときに表示されるプライマリイメージです。

   * このメソッドの構文を次に示します。

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
