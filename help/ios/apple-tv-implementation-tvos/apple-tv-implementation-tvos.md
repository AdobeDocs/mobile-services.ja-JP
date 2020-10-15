---
description: tvOS を使用した Apple TV を実装するのに役立つ情報です。
seo-description: tvOS を使用した Apple TV を実装するのに役立つ情報です。
seo-title: tvOS を使用した Apple TV 実装
solution: Experience Cloud,Analytics
title: tvOS を使用した Apple TV 実装
topic: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '402'
ht-degree: 100%

---


# tvOS を使用した Apple TV 実装 {#apple-tv-implementation-with-tvos}

tvOS を使用した Apple TV を実装するのに役立つ情報です。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## 概要

新しい Apple TV では、アプリケーションを作成してネイティブ tvOS 環境で実行できるようになりました。iOS で利用可能ないくつかのフレームワークを使用してネイティブなアプリを作成するか、XML テンプレートおよび JavaScript を使用してアプリを作成できます。

>[!TIP]
>
>tvOS のサポートは、`AdobeMobileLibrary`バージョン 4.7.0 以降で利用可能になりました。

## はじめに {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>tvOS をターゲットとする Apple TV アプリがプロジェクトのターゲットとして存在すると想定しています。詳しくは、[tvOS](https://developer.apple.com/tvos/documentation/) を参照してください。

## tvOS のネイティブアプリの設定 {#section_5095F19B3C4545F68E8C1E37A7E303AE}

次の手順を Xcode プロジェクトで実行します。

1. AdobeMobileLibrary フォルダーをプロジェクトにドラッグします。
1. `ADBMobileConfig.json` ファイルがターゲットのメンバーであることを確認します。
1. tvOS アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**[!UICONTROL Link Binary with Libraries]**」セクションを展開して、以下のライブラリを追加します。

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

詳しくは、[iOS](https://developer.apple.com/ios/resources/) に記載されている iOS ドキュメントを参照してください。

## TVML／TVJS アプリの tvOS 向け設定 {#section_AB2EC8C326654F3387658EBBD990BB12}

1. `AdobeMobileLibrary` フォルダーをプロジェクトにドラッグします。
1. `ADBMobileConfig.json` ファイルがターゲットのメンバーであることを確認します。
1. tvOS アプリのターゲットの「**[!UICONTROL Build Phases]**」タブで、「**[!UICONTROL Link Binary with Libraries]**」セクションを展開して、以下のライブラリを追加します。

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. `TVApplicationControllerDelegate` クラスの実装ファイルで、SDK をインポートします。

   ```objective-c
   #import “ADBMobile.h"
   ```

1. `TVApplicationControllerDelegate` クラスの `application:didFinishLaunchWithOptions:` メソッドで、`installTVMLHooks:` メソッドを使用して `TVApplicationController` オブジェクトを SDK に渡します。

   Adobe SDK は、アプリの `TVApplicationController` にアクセスして、Adobe SDK をアプリの JSContext に登録する必要があります。この手順を使用して、JavaScript ファイルから Adobe SDK のネイティブメソッドを呼び出すことができます。

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. JavaScript ファイル内で、`ADBMobile` オブジェクトを使用して、Adobe SDK のネイティブメソッドにアクセスします。

   使用可能なメソッドの詳細な一覧は、「[TVJS メソッド](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md)」を参照してください。

