---
description: 状態とは、アプリケーションの様々な画面またはビューのことです。アプリケーションで新しい状態が表示されるたびに（ユーザーがホームページからニュースフィードに移動する場合など）、trackState コールを送信する必要があります。iOS の場合、一般的に、状態は各ビューの viewDidLoad メソッドで追跡されます。
seo-description: 状態とは、アプリケーションの様々な画面またはビューのことです。アプリケーションで新しい状態が表示されるたびに（ユーザーがホームページからニュースフィードに移動する場合など）、trackState コールを送信する必要があります。iOS の場合、一般的に、状態は各ビューの viewDidLoad メソッドで追跡されます。
seo-title: アプリの状態の追跡
solution: Marketing Cloud、Analytics
title: アプリの状態の追跡
topic: 開発者と導入
uuid: 12cca4eb-1f15-4cec- a58f-76b69eaff99d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# アプリの状態の追跡 {#track-app-states}

状態とは、アプリケーションの様々な画面またはビューのことです。アプリケーションで新しい状態が表示されるたびに（ユーザーがホームページからニュースフィードに移動する場合など）、trackState コールを送信する必要があります。iOS の場合、一般的に、状態は各ビューの viewDidLoad メソッドで追跡されます。

>[!TIP]
>
>To track states, make a call to `trackState`. 状態は、自動的には追跡されません。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackState` を呼び出して、この状態ビューのヒットを送信します。

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In Adobe Mobile services, the **[!UICONTROL State Name]** is reported in the *`View State`* variable, and a view is recorded for each `trackState` call. その他の Analytics インターフェイスでは、**[!UICONTROL View State]** は **[!UICONTROL Page Name]** としてレポートされ、state views は page views としてレポートされます。

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

**[!UICONTROL State Name]**&#x200B;に加えて、各trackアクション呼び出しで追加のコンテキストデータを送信できます。

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

コンテキストデータ値は、カスタム変数にマップする必要があります。

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

通常、状態はパスレポートを使用して表示されるので、ユーザーがアプリ内をどのように移動しているか、どの状態が最も多く閲覧されているかを確認できます。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 画面遷移]レポート。**&#x200B;このレポートは、ユーザーがアプリケーション内でたどったパスに基づきます。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 状態は、**ページ**&#x200B;レポート、**[!UICONTROL ページビュー数]**&#x200B;レポート、**パス[!UICONTROL レポートなど、ページを確認できる場所であればどこでも確認できます。]** |
| ad hoc analysis | 状態は、**ページ**&#x200B;ディメンション、**[!UICONTROL ページビュー数]**&#x200B;指標、**パス[!UICONTROL レポートを使用してページを確認できる場所であればどこでも確認できます。]** |
