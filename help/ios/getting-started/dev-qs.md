---
description: iOS ライブラリの実装や、起動、アップグレード、セッション、関与ユーザーといったライフサイクル指標の収集に役立つ情報です。
seo-description: iOS ライブラリの実装や、起動、アップグレード、セッション、関与ユーザーといったライフサイクル指標の収集に役立つ情報です。
seo-title: コア実装とライフサイクル
solution: Marketing Cloud,Analytics
title: コア実装とライフサイクル
topic: 開発者と導入
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: tm+mt
source-git-commit: be980e0e639d5b0df3f1b6a6f91f3ad0a5efe8d7

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

iOS ライブラリの実装や、起動、アップグレード、セッション、関与ユーザーといったライフサイクル指標の収集に役立つ情報です。

## SDK のダウンロード {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**前提条件**

SDKをダウンロードする前に、 *Core実装およびライフサイクルのレポートスイートの作成の手順を実行して*[](/help/ios/getting-started/requirements.md) 、開発レポートスイートを設定し、設定ファイルの事前入力バージョンをダウンロードします。

SDK をダウンロードするには

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`：iOS AppMeasurement に使用する Objective-C ヘッダーファイル。
   * `ADBMobileConfig.json`：アプリ用にカスタマイズされた SDK 設定ファイル。
   * `AdobeMobileLibrary.a`、iOSデバイス用のライブラリビルド(armv7、armv7s、arm64)とシミュレーター(i386、x86_64)を含む、ビットコード対応の大きなバイナリ。

      ターゲットが iOS アプリを対象としている場合は、このファットバイナリがリンクされている必要があります。

   * `AdobeMobileLibrary_Extension.a`：iOS デバイス用のライブラリビルド（armv7、armv7s、arm64）とシミュレーター（i386 および x86_64）を含む、ビットコード対応のファットバイナリ。

      ターゲットが iOS エクステンションを対象としている場合は、このファットバイナリがリンクされている必要があります。

   * `AdobeMobileLibrary_Watch.a`：Apple Watch デバイス用のライブラリビルド（armv7k）とシミュレーター（i386 および x86_64）を含む、ビットコード対応のファットバイナリ。

      ターゲットが Apple Watch（watchOS 2）エクステンションアプリを対象としている場合は、このファットバイナリがリンクされている必要があります。

   * `AdobeMobileLibrary_TV.a`：新しい Apple TV デバイス用のライブラリビルド（arm64）とシミュレーター（x86_64）を含む、ビットコード対応のファットバイナリ。

      ターゲットが Apple TV（tvOS）アプリを対象としている場合は、このファットバイナリがリンクされている必要があります。

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Xcode IDE を起動して、アプリを開きます。
1. プロジェクトナビゲーターで、`AdobeMobileLibrary` フォルダーをドラッグして、プロジェクトにドロップします。
1. 以下を確認します。

   * 「**[!UICONTROL Copy Items if Needed]」チェックボックスがオンになっている。**
   * **[!UICONTROL 「Create Groups]**」がオンになっている。
   * 「**[!UICONTROL Add to targets]」セクションのチェックボックスがすべてオフになっている。**
   ![](assets/step_3.png)

1. Click **[!UICONTROL Finish]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. アプリをクリックします。
   1. 「**[!UICONTROL General]**」タブで、ターゲットを選択し、「**[!UICONTROL Linked Frameworks]and** Libraries **」セクションで、必要なフレームワークおよびライブラリをリンクします。**
   * **iOS App Targets**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **iOS エクステンションのターゲット**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch（watchOS 2）のターゲット**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV（tvOS）のターゲット**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. アプリがエラーなくビルドされることを確認します。

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

次に/ `collectLifecycleData`呼び出し `collectLifecycleDataWithAdditionalData` を追加しま `application:didFinishLaunchingWithOptions`す。

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### ライフサイクル呼び出しに追加のデータを含める

追加データをライフサイクル指標コールに含めるには、`collectLifecycleDataWithAdditionalData` : を使用します。

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. SDK は、`NSDictionary` 型または `NSString` 型ではない `NSNumber` パラメーターの値を削除します。

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

`collectLifecycleDataWithAdditionalData` で送信される追加のコンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-lifecycle.png)

その他のライフサイクル指標は自動的に収集されます。詳しくは、 [ライフサイクル指標](/help/ios/metrics.md).

## 次の作業 {#section_A24DC703359D4B5C8F493D6421306FD3}

次のタスクを実行します。

* [アプリの状態の追跡](/help/ios/analytics-main/states.md)
* [アプリのアクションの追跡](/help/ios/analytics-main/actions.md)
