---
description: WatchOS 2 以降、Apple Watch で WatchKit エクステンションを実行できます。この環境で動作するアプリケーションが iOS 本体アプリとデータを共有するには、WatchConnectivity フレームワークが必要です。
solution: Experience Cloud Services,Analytics
title: WatchOS 2 を使用した Apple Watch 実装
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 100%

---

# WatchOS 2 を使用した Apple Watch 実装 {#apple-watch-implementation-with-watchos}

WatchOS 2 以降、WatchKit エクステンションを Apple Watch で実行できます。この環境で動作するアプリケーションが iOS 本体アプリとデータを共有するには、`WatchConnectivity` フレームワークが必要です。

>[!TIP]
>
>`AdobeMobileLibrary` v4.6.0 以降、`WatchConnectivity` がサポートされます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## はじめに {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>少なくとも以下のターゲットを持つプロジェクトがあることを確認します。
>
>* 本体アプリ
>* WatchKit アプリ
>* WatchKit 拡張
>


WatchKit アプリの開発について詳しくは、「[Watch App アーキテクチャ](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1)」を参照してください。

## 本体アプリの設定 {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

次の手順を Xcode プロジェクトで実行します。

1. `AdobeMobileLibrary` フォルダーをプロジェクトにドラッグします。
1. `ADBMobileConfig.json` ファイルが本体アプリのターゲットのメンバーであることを確認します。
1. 本体アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**[!UICONTROL Link Binary with Libraries]**」セクションを展開して、以下のライブラリを追加します。

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
   #import "ADBMobile.h"
   ```

1. `ADBMobile` ライブラリを呼び出す前に、AppDelegate の `application:didFinishLaunchingWithOptions:`で、`WCSession` を設定します。

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. AppDelegate で、`session:didReceiveMessage:` と `session:didReceiveUserInfo:` メソッドを実装します。

   `syncSettings:` は `ADBMobile` ライブラリ内で呼び出され、`ADBMobile` ライブラリが使用する目的で辞書が作成されたかどうかを示すブール値を返します。`No` を返す場合、メッセージは Adobe SDK から開始されたものではありません。

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

## WatchKit エクステンションの設定 {#section_5ADE31741E514330A381F2E3CFD4A814}

1. `ADBMobileConfig.json` ファイルが WatchKit エクステンションのターゲットのメンバーであることを確認します。
1. WatchKit エクステンションのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**[!UICONTROL Link Binary with Libraries]**」セクションを展開して、以下のライブラリを追加します。

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. `WKExtensionDelegate` プロトコルを実装するクラスで、`WatchConnectivity` を読み込み、`WCSessionDelegate` プロトコルを追加します。

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. ExtensionDelegate クラスの実装ファイル内で、`AdobeMobileLibrary` を読み込みます。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `applicationDidFinishLaunching` ライブラリへのコールをおこなう前に、ExtensionDelegate の `WCSession` で、`ADBMobile` を設定します。

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

1. ExtensionDelegate で、`session:didReceiveMessage:` メソッドと `session:didReceiveUserInfo:` メソッドを実装します。

   `syncSettings:` は `ADBMobile` ライブラリ内で呼び出され、`ADBMobile` ライブラリが使用する目的で辞書が作成されたかどうかを示すブール値を返します。`NO` を返す場合、メッセージは Adobe SDK から開始されたものではありません。

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

* WatchKit アプリの場合、`a.RunMode` は `Extension` に設定されます。
* WatchKit アプリは腕時計で実行されるので、`a.AppID` に名前が正しくレポートされます。
* WatchOS2 アプリに対しては、ライフサイクルコールはトリガーされません。
