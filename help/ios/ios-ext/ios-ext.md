---
description: iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。
seo-description: iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。
seo-title: iOS エクステンション実装
solution: Experience Cloud,Analytics
title: iOS エクステンション実装
topic: 開発者と導入
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# iOS エクステンション実装 {#ios-extension-implementation}

iOS エクステンションを使用して、Apple Watch アプリ（WatchOS 1）、Today ウィジェット、Photo Editing ウィジェットおよびその他の iOS エクステンションアプリから使用状況データを収集できます。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合、最新のドキュメントについては、[こちら](https://aep-sdks.gitbook.io/docs/)をクリックしてください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

## 独自のラッパーに代わる iOS SDK の使用に関する推奨事項 {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>独自のラッパーではなく、iOS SDK を使用することをお勧めします。

Apple は、本体アプリにリクエストを送信し、応答を受信することによって Watch アプリと本体アプリとの通信を可能にする API のセットを提供しています。Watch アプリから本体アプリに辞書としてトラッキングデータを送信し、本体アプリに対してトラッキングメソッドを呼び出してデータを送信することは可能ですが、この方法には限界があります。

ほとんどの場合、Watch アプリの使用時には本体アプリがバックグラウンドで実行されているので、安全に呼び出せるメソッドは `TrackLocation`、`TrackActionInBackground`、`TrackBeacon` の 3 つのみとなります。他のトラッキングメソッドはライフサイクルデータに干渉するので、Watch アプリからデータを送信する際には使用できません。

Watch アプリ向けの SDK には、アプリ内メッセージ以外のすべてのモバイル機能が含まれています。そのため、上記の 3 つのトラッキングメソッドで必要なデータを収集できる場合であっても、iOS SDK を使用してください。

## はじめに {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>少なくとも以下のターゲットを持つプロジェクトがあることを確認します。
>
>* アプリを収容する 1 つのターゲット。
>* エクステンション用の 1 つのターゲット。
>



WatchKit アプリを使用する場合は、3 つ目のターゲットが必要です。Apple Watch 用の開発について詳しくは、「[Apple Watch 用の開発](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)」を参照してください。

## 含まれるアプリの設定 {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

次の手順を Xcode プロジェクトで実行します。

1. AdobeMobileLibrary フォルダーをプロジェクトにドラッグします。
1. `ADBMobileConfig.json` ファイルが本体アプリのターゲットのメンバーであることを確認します。
1. 本体アプリのターゲットの&#x200B;**[!UICONTROL Build Phases]**&#x200B;タブで、**[!UICONTROL Link Binary with Libraries]**&#x200B;セクションを展開して、以下のライブラリを追加します。

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. 本体アプリのターゲットの&#x200B;**[!UICONTROL Capabilities]**&#x200B;タブを開き、**[!UICONTROL App Groups]**&#x200B;を有効にして、新しいアプリグループ（例：`group.com.adobe.testAp`）を追加します。

1. AppDelegate で、Adobe Mobile ライブラリとやり取りをおこなう前に、アプリグループを `application:didFinishLaunchingWithOptions` に設定します。

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

##  拡張機能の設定{#section_28C994B7892340AC8D1F07AF26FF3946}

1. `ADBMobileConfig.json` ファイルがエクステンションのターゲットのメンバーであることを確認します。
1. エクステンションのターゲットの&#x200B;**[!UICONTROL Build Phases]**&#x200B;タブで、**[!UICONTROL Link Binary with Libraries]**&#x200B;セクションを展開して、以下のライブラリを追加します。

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. エクステンションのターゲットの&#x200B;**[!UICONTROL Capabilities]**&#x200B;タブを開き、**[!UICONTROL App Groups]**&#x200B;を有効にして、上記の「*本体アプリの設定*」の手順 4 で追加したアプリグループを選択します。

1. InterfaceController で、Adobe Mobile ライブラリとその他のやり取りをおこなう前に、アプリグループを `awakeWithContext:` に設定します。

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. アプリが予期せぬエラーなくビルドされることを確認します。

## 追加情報 {#section_21497E81231549CB9F164DEECFF5BA0D}

以下の情報を覚えておいてください。

* データの取得元が本体アプリかエクステンションかを示すためのコンテキストデータ値 `a.RunMode` が追加されました。

   * `a.RunMode = Application`

      この値は、ヒット元が本体アプリであることを意味します。
   * `a.RunMode = Extension`

      この値は、ヒット元がエクステンションであることを意味します。

* SDK の以前のバージョンからアップグレードする場合、本体アプリを起動すると、すべてのユーザーデフォルト値とキャッシュされているファイルが、本体アプリのフォルダーからアプリグループの共有フォルダーに自動的に移行されます。
* 本体アプリが起動されない場合、エクステンションからのヒットは破棄されます。
* バージョン番号とビルド番号は、本体アプリとエクステンションアプリ間で同じである必要があります。
* iOS エクステンションアプリに対してライフサイクルコールはトリガーされません。

