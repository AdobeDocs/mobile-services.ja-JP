---
description: WatchOS 2 以降、WatchKit エクステンションが Apple Watch 端末で動作するようになります。この環境で動作するアプリケーションが iOS 本体アプリとデータを共有するには、WatchConnectivity フレームワークが必要です。
seo-description: WatchOS 2 以降、WatchKit エクステンションが Apple Watch 端末で動作するようになります。この環境で動作するアプリケーションが iOS 本体アプリとデータを共有するには、WatchConnectivity フレームワークが必要です。
seo-title: WatchOS 2 を使用した Apple Watch 実装
solution: Marketing Cloud,Analytics
title: WatchOS 2 を使用した Apple Watch 実装
topic: 開発者と導入
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

WatchOS 2以降では、WatchKit拡張機能をApple Watch上で実行できます。 Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>v4.6.0 `AdobeMobileLibrary` 以降はサポートさ `WatchConnectivity` れています。

## New Adobe Experience Platform Mobile SDK Release

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launchに移動します。
* Experience Platform SDK リポジトリの内容については、[Github：Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## はじめに {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>少なくとも次のターゲットを持つプロジェクトがあることを確認します。
>
>* 本体アプリ
>* WatchKit アプリ
>* WatchKit エクステンション
>



WatchKit アプリの開発について詳しくは、[Watch App のアーキテクチャ](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)を参照してください。

## 含まれるアプリの設定 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

次の手順を Xcode プロジェクトで実行します。

1. `AdobeMobileLibrary` フォルダーをプロジェクトにドラッグします。
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. 本体アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. `UIApplicationDelegate` プロトコルを実装するクラスで、`WCSessionDelegate` プロトコルを追加します。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. AppDelegate クラスの実装ファイル内で、`AdobeMobileLibrary` をインポートします。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` がライブラリ内で呼び出さ `ADBMobile` れ、ディクショナリがライブラリでの使用を目的としているかどうかを示すboolが返さ `ADBMobile` れます。 `No` を返す場合、メッセージは Adobe SDK から開始されたものではありません。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## WatchKit拡張の設定 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. WatchKit エクステンションのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**Link Binary with Libraries]」セクションを展開して、以下のライブラリを追加します。[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. ExtensionDelegate クラスの実装ファイル内で、`AdobeMobileLibrary` をインポートします。

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. ExtensionDelegate の `applicationDidFinishLaunching` で、SDK 用に Watch App を初期化します。

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` がライブラリ内で呼び出さ `ADBMobile` れ、ディクショナリがライブラリでの使用を目的としているかどうかを示すboolが返さ `ADBMobile` れます。 `NO` を返す場合、メッセージは Adobe SDK から開始されたものではありません。

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## 追加情報 {#section_7BCDB5CF0D424DCA97883753D1881233}

次の情報に留意してください。

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* WatchKit アプリは腕時計で実行されるので、`a.AppID` に名前が正しくレポートされます。
* WatchOS2 アプリに対しては、ライフサイクルコールはトリガーされません。

