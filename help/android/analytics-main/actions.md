---
description: アクションは、Android アプリ内で発生し、測定対象となるイベントです。
seo-description: アクションは、Android アプリ内で発生し、測定対象となるイベントです。
seo-title: アプリのアクションの追跡
solution: Experience Cloud,Analytics
title: アプリのアクションの追跡
topic-fix: Developer and implementation
uuid: fe01c1df-f6bb-4b32-b3ef-959d2c724af6
exl-id: 495a6aa8-781d-4499-ad46-e19d57cccf40
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 100%

---

# アプリのアクションの追跡 {#track-app-actions}

アクションは、Android アプリ内で発生し、測定対象となるイベントです。

各アクションには、イベントが発生するたびに増分される、1 つ以上の対応する指標があります。例えば、新規サブスクリプションごとに、記事が表示されるたびに、レベルが完了するたびに、`trackAction` 呼び出しを送信します。アクションは自動的には追跡されないので、追跡するイベントが発生したときに `trackAction` を呼び出し、アクションをカスタムイベントにマップする必要があります。

## アクションのトラッキング {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. 追跡するアクションがアプリで発生したら、`trackAction` を呼び出して、このアクションのヒットを送信します。

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Adobe Mobile Services UI で、アプリを選択し、「**[!UICONTROL アプリ設定]**」をクリックします。
1. 「**[!UICONTROL 変数と指標の設定]**」をクリックしてから、「**[!UICONTROL カスタム指標]**」タブをクリックします。

1. コードに定義されているコンテキストデータ名（例えば、`myapp.ActionName`）をカスタムイベントにマッピングします。

   ![](assets/map-event-context-data.png)

すべてのアクション値を保持する prop を設定することもできます。そのためには、「**[!UICONTROL カスタムアクション]**」などの名前のカスタム prop をマッピングし、値を `a.action` に設定します。

![](assets/map-custom-prop.png)

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

アクション名に加え、各 trackAction コールとともに追加のコンテキストデータを送信できます。

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

コンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-action.png)

## アクションレポート {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| インターフェイス | レポート |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL アクションパス]**&#x200B;レポート。アプリでアクションが発生する順序を表示します。任意のレポートで「**[!UICONTROL カスタマイズ]**」をクリックすると、ランク付け、トレンド表示または分類レポートでアクションを表示したり、フィルターを適用して特定のセグメントのアクションを表示したりできます。 |
| マーケティングレポートと分析 | **[!UICONTROL カスタムイベント]**&#x200B;レポート。アクションがカスタムイベントにマップされた後、他のすべての Analytics イベントと同様にモバイルイベントを表示できます。 |
| アドホック分析 | **[!UICONTROL カスタムイベント]**&#x200B;レポート。アクションがカスタムイベントにマップされた後、他のすべての Analytics イベントと同様にモバイルイベントを表示できます。 |
