---
description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。ユーザーが生成されたリンクをクリックしてアプリストアからアプリをダウンロードして実行すると、SDKは自動的に獲得データを収集してAdobe Mobileサービスに送信します。
keywords: android;library;mobile;sdk
seo-description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。ユーザーが生成されたリンクをクリックしてアプリストアからアプリをダウンロードして実行すると、SDKは自動的に獲得データを収集してAdobe Mobileサービスに送信します。
seo-title: モバイルアプリの獲得
solution: Marketing Cloud、Analytics
title: モバイルアプリの獲得
topic: 開発者と導入
uuid: 4d32cae9- e856-4e40-8a29-2b5bpcp106e0
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile app acquisition {#mobile-app-acquisition}

Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。ユーザーが生成されたリンクをクリックしてアプリストアからアプリをダウンロードして実行すると、SDKは自動的に獲得データを収集してAdobe Mobileサービスに送信します。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、[Launch](https://launch.adobe.com/) にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。For more information about using Acquisition and Marketing Links with the Experience Cloud SDKs, see [Acquisition and Marketing Links](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#acquisition-and-marketing-links).

>[!IMPORTANT]
>
>獲得機能を使用するには、SDK バージョン 4.1 以降が&#x200B;**必要**&#x200B;です。

ダウンロード計測用リンクは Adobe Mobile Services で作成する必要があります。For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**SDK バージョン 4.13.1 以降**：

Adobe Mobile Services で作成されたダウンロード計測用リンクを使用できない場合でも、Google Play Acquisition を使用して、SDK で獲得データを収集し、送信することができます。

標準の Google Play Acquisition キャンペーンから獲得データを収集するには：

* 標準の Google Play ストアの獲得方法を使用します。

   カスタム獲得データは、標準の Google Play Acquisition のキーと値のペアで使用できます。

* ユーザーが Google Play ストアの獲得の結果としてアプリをダウンロードして実行すると、リファラーからのデータが収集され、Adobe Mobile Services に送信されます。

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      詳しくは [、設定メソッド](/help/android/configuration/methods.md)を参照してください。

   * また `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL``MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` はイベントタイプを使用します。

   * Google Play の獲得データに含まれていたカスタムキーには、「`a.acquisition.custom.`」という名前空間が設定されます。

Adobe Mobile Services で作成されたダウンロード計測用リンクを使用している場合は、次のタスクを実行して、カスタムデータをダウンロード計測用リンクに追加します。

1. 獲得変数の先頭にプレフィックス「`adb`」を付けます。

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. また `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL``MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` はイベントタイプが使用されます。

1. カスタムデータキーには"`a.acquisition.custom.`

>[!TIP]
>
>複数のレポートスイートにデータを送信する場合は、レポートスイートIDのリストにある最初のレポートスイートに関連付けられているアプリから、獲得データを使用します。

このセクションの更新により、SDK はダウンロード計測用リンクから獲得データを送信できます。

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [、"SDKおよび設定ファイルのIntelliJ IDEAまたはEclipseプロジェクトへの追加」を参照](/help/android/getting-started/dev-qs.md)してください。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. リファラーの `BroadcastReceiver` を実装します。

   ```java
   package com.your.package.name;  // replace with your app package name 
   
   import android.content.BroadcastReceiver; 
   import android.content.Context; 
   import android.content.Intent; 
   
   public class GPBroadcastReceiver extends BroadcastReceiver { 
     @Override 
     public void onReceive(Context c, Intent i) { 
      com.adobe.mobile.Analytics.processReferrer(c, i); 
     } 
   }
   ```

1. `AndroidManifest.xml` を更新して、前の手順で作成した `BroadcastReceiver` を有効にします。

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
    <intent-filter> 
     <action android:name="com.android.vending.INSTALL_REFERRER" /> 
    </intent-filter> 
   </receiver>
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >複数のレポートスイートにデータを送信する場合は、レポートスイートIDのリストにある最初のレポートスイートに関連付けられたアプリから、獲得設定（獲得サーバーとappid）を使用します。

   `acquisition` 設定は Adobe Mobile Services によって生成されます。この設定を変更しないでください。For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

これらの設定を有効にすると、アプリを初めて起動した後、最初のライフサイクル呼び出しで獲得データが自動的に送信されます。

>[!CAUTION]
>
>`referrerTimeout` を0より大きい値に設定して、アプリの獲得を有効にする必要があります。
