---
description: 解析データやイベントからトリガーされるアプリ内メッセージを配信できます。 実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。
seo-description: 解析データやイベントからトリガーされるアプリ内メッセージを配信できます。 実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。
seo-title: アプリ内メッセージ
solution: Marketing Cloud,Analytics
title: アプリ内メッセージ
topic: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 61%

---


# アプリ内メッセージ {#in-app-messaging}

解析データやイベントからトリガーされるアプリ内メッセージを配信できます。 実装後、メッセージはアプリに動的に配信され、コードを更新する必要はありません。

## 新しい Adobe Experience Cloud SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

>[!IMPORTANT]
>
>2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* To get started, go to [Launch](https://launch.adobe.com/).
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> Adobe Experience Platform Mobile SDK を Adobe Launch で使用している場合、アプリ内メッセージおよびプッシュ通知などの機能を使用するには、Adobe Analytics Mobile Services 拡張機能もインストールする&#x200B;**必要があります**。詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。Experience Cloud SDK でのプッシュメッセージおよびアプリ内メッセージの使用について詳しくは、「[プッシュメッセージの設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging)」および「[アプリ内メッセージの設定](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging)」を参照してください。

>[!IMPORTANT]
>
>To use in-app messaging, you **must** have SDK version 4.2 or later.

Adobe Mobile Servicesでは、メッセージや、メッセージを表示するタイミングを定義するルールを作成できます。 For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). アプリ内メッセージを表示するには、SDKを更新する必要があります。 メッセージをまだ定義していない場合でも、これらの手順を実行できます。 定義したメッセージは、アプリに動的に配信され、アプリストアを更新しなくても表示されます。

## アプリ内メッセージの有効化 {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. `AndroidManifest.xml` ファイルを更新して、フルスクリーンアクティビティを宣言し、メッセージ通知ハンドラーを有効にします。

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

1. アプリ内メッセージに必要な設定が `ADBMobileConfig.json` ファイルに含まれていることを確認します。

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

   このオブジェクトが設定されていない場合は、更新された `ADBMobileConfig.json` ファイルを Adobe Mobile Services からダウンロードしてください。詳しくは、[事前準備](/help/android/getting-started/requirements.md)を参照してください。

## アプリ内メッセージの追跡 {#section_B85CDF6929564AAEA79338B55E5CB1E8}

AndroidモバイルSDKは、アプリ内メッセージに関する以下の指標を追跡します。

* アプリ内メッセージのフルスクリーンおよび警告スタイルの場合：

   * **インプレッション**: ユーザーがアプリ内メッセージをトリガーしたとき。
   * **クリックスルー**：ユーザーが&#x200B;**[!UICONTROL クリックスルー]**&#x200B;ボタンを押したとき。
   * **キャンセル**：ユーザーが&#x200B;**[!UICONTROL キャンセル]**&#x200B;を押したとき。

* カスタムの全画面アプリ内メッセージの場合は、メッセージ内の HTML コンテンツに次のボタンに関する SDK 追跡を通知する正しいコードが含まれている必要があります。

   * **クリックスルー**（リダイレクト）のトラッキング例：

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **キャンセル**（終了）追跡の例：

      `adbinapp://cancel`

## ローカルフォールバック画像 {#section_DEACC1CE549B4573B556A44A52409941}

フルスクリーンメッセージを作成する場合、必要に応じてフォールバック画像を指定できます。 メッセージがWebから目的の画像を取得できない場合、SDKは、アプリケーションのアセットフォルダーから同じ名前の画像を読み込もうとします。 これにより、ユーザーがオフラインの場合や、事前に決められている画像が未到達の場合でも、メッセージを元の形式で表示できます。

>[!IMPORTANT]
>
>フォールバック画像アセット名は、Adobe Mobile Services でメッセージを設定するときに指定されます。指定されたリソースが使用可能であることを確認する必要があります。

## 通知アイコンの設定 {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

次のメソッドを使用すると、通知領域に表示される小さいアイコンと大きいアイコンのほか、通知ドロワーに通知が表示されたときに表示される大きいアイコンを設定できます。

* **Config.setSmallIconResourceId(int resourceId)**

   SDKで作成される通知に使用する小さいアイコンを設定します。 このアイコンは、ステータスバーに表示され、ユーザーが通知センターで通知を完了したときに表示されるセカンダリイメージです。

   * このメソッドの構文を次に示します。

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   SDK で作成される通知に使用される大きいアイコンを設定します。このアイコンは、ユーザーが通知センターで完全な通知を表示する際に表示されるプライマリ画像です。

   * このメソッドの構文を次に示します。

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
