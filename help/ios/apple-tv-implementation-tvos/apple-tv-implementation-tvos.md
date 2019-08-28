---
description: tvOS を使用した Apple TV を実装するのに役立つ情報です。
seo-description: tvOS を使用した Apple TV を実装するのに役立つ情報です。
seo-title: tvOS を使用した Apple TV 実装
solution: Marketing Cloud、Analytics
title: tvOS を使用した Apple TV 実装
topic: 開発者と導入
uuid: d1571ea2- a5de-4b96- a527-72abbf51fb8
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

tvOS を使用した Apple TV を実装するのに役立つ情報です。

## Adobe Experience Cloud SDK の新規リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 利用を開始するには、Launch にアクセスしてください。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. 詳しくは、「[Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)」を参照してください。

Apple TV では、ネイティブ tvOS 環境で動作するアプリケーションを作成できるようになりました。iOS で利用可能ないくつかのフレームワークを使用してネイティブなアプリを作成することも、XML テンプレートおよび JavaScript を使用してアプリを作成することもできます。

>[!TIP]
>
>tvOSのサポートはバージョン4.7.0から `AdobeMobileLibrary` 開始できます。

## はじめに {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>プロジェクトにターゲットtvOSのApple TVアプリがあると想定します。詳しくは、[tvOS](https://developer.apple.com/tvos/documentation/) を参照してください。

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

次の手順を Xcode プロジェクトで実行します。

1. AdobeMobileLibrary フォルダーをプロジェクトにドラッグします。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. tvOS アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

詳しくは、[iOS](https://developer.apple.com/ios/resources/) に記載されている iOS ドキュメントを参照してください。

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. `AdobeMobileLibrary` フォルダーをプロジェクトにドラッグします。
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. tvOS アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. `TVApplicationControllerDelegate` クラスの実装ファイルで、SDK をインポートします。

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Adobe SDK は、アプリの `TVApplicationController` にアクセスして、Adobe SDK をアプリの JSContext に登録する必要があります。この手順を使用して、JavaScript ファイルから Adobe SDK のネイティブメソッドを呼び出すことができます。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. JavaScript ファイル内で、`ADBMobile` オブジェクトを使用して、Adobe SDK のネイティブメソッドにアクセスします。

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

