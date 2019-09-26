---
description: iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。
seo-description: iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。
seo-title: iOS エクステンション実装
solution: Marketing Cloud,Analytics
title: iOS エクステンション実装
topic: 開発者と導入
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# iOS extension implementation {#ios-extension-implementation}

iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。

## New Adobe Experience Platform Mobile SDK Release

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* To get started, go to Adobe Experience Platform Launch.
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>ラッパーではなくiOS SDKを使用することを強くお勧めします。

Apple は、本体アプリにリクエストを送信し、応答を受信することによって Watch アプリと本体アプリとの通信を可能にする API のセットを提供しています。Watch アプリから本体アプリに辞書としてトラッキングデータを送信し、本体アプリに対してトラッキングメソッドを呼び出してデータを送信することは可能ですが、この方法には限界があります。

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. 他のトラッキングメソッドはライフサイクルデータに干渉するので、Watch アプリからデータを送信する際には使用できません。

Watch アプリ向けの SDK には、アプリ内メッセージ以外のすべてのモバイル機能が含まれています。そのため、上記の 3 つのトラッキングメソッドで必要なデータを収集できる場合であっても、iOS SDK を使用してください。

## はじめに {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>少なくとも次のターゲットを持つプロジェクトがあることを確認します。
>
>* アプリを収容する 1 つのターゲット。
>* エクステンション用の 1 つのターゲット。
>



WatchKit アプリを使用する場合は、3 つ目のターゲットが必要です。For more information on developing for Apple Watch, see Developing for Apple Watch.[](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)

## Configure the containing app {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

次の手順を Xcode プロジェクトで実行します。

1. AdobeMobileLibrary フォルダーをプロジェクトにドラッグします。
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. 本体アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. AppDelegate で、Adobe Mobile ライブラリとやり取りをおこなう前に、アプリグループを `application:didFinishLaunchingWithOptions` に設定します。

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

##  拡張機能の設定{#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. エクステンションのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

覚えておく必要がある情報を以下に示します。

* データの取得元が本体アプリかエクステンションかを示すためのコンテキストデータ値 `a.RunMode` が追加されました。

   * `a.RunMode = Application`

      この値は、ヒット元が本体アプリであることを意味します。
   * `a.RunMode = Extension`

      この値は、ヒット元がエクステンションであることを意味します。

* SDK の以前のバージョンからアップグレードする場合、本体アプリを起動すると、すべてのユーザーデフォルト値とキャッシュされているファイルが、本体アプリのフォルダーからアプリグループの共有フォルダーに自動的に移行されます。
* 本体アプリが起動されない場合、エクステンションからのヒットは破棄されます。
* バージョン番号とビルド番号は、本体アプリとエクステンションアプリ間で同じである必要があります。
* iOS エクステンションアプリに対してライフサイクルコールはトリガーされません。

