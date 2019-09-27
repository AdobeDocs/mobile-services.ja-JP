---
description: 状態とは、アプリケーションの様々な画面または表示のことです。
seo-description: 状態とは、アプリケーションの様々な画面または表示のことです。
seo-title: アプリの状態の追跡
solution: Marketing Cloud,Analytics
title: アプリの状態の追跡
topic: 開発者と導入
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# アプリの状態の追跡 {#track-app-states}

状態とは、アプリケーションの様々な画面または表示のことです。

アプリケーションで新しい状態が表示されるたびに（例えば、ユーザーがホームページからニュースフィードに移動する場合）、`trackState` 呼び出しが送信されます。Android では通常、`trackState` は、新しいアクティビティが読み込まれるたびに呼び出されます。

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、 *Core実装およびライフサイクルのIntelliJ IDEAまたはEclipse ProjectへのSDKと設定ファイルの追加*[を参照してください](/help/android/getting-started/dev-qs.md)。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. `onCreate` 関数で、`trackState` を呼び出して、この状態ビューのヒットを送信します。

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces, `View State` is reported as `Page Name`, and `state views` is reported as `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

`"State Name"` に加えて、各アクション追跡呼び出しを使用して追加のコンテキストデータを送信することができます。

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

コンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

状態を確認するには、通常、パスレポートを使用します。このレポートでは、ユーザーがアプリ内をどのように移動したかや、最も頻繁に表示されたのはどの状態であるかがわかります。

|  |  |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL 画面遷移]レポート。**&#x200B;このレポートは、ユーザーがアプリケーション内でたどったパスに基づきます。A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | 状態は、**ページ**&#x200B;レポート、**[!UICONTROL ページビュー数]**&#x200B;レポート、**パス[!UICONTROL レポートなど、ページを確認できる場所であればどこでも確認できます。]** |
| ad hoc analysis | 状態は、**ページ**&#x200B;ディメンション、**[!UICONTROL ページビュー数]**&#x200B;指標、**パス[!UICONTROL レポートを使用してページを確認できる場所であればどこでも確認できます。]** |


