---
description: アクションは、アプリ内で発生し、測定対象となるイベントです。各アクションには、イベントが発生するたびに増分される、1 つ以上の対応する指標があります。例えば、記事が表示されるたび、またはレベルが完了するたびに、新規サブスクリプションを追跡します。これらのイベントに対応する指標は、サブスクリプション、読み取った記事、完了したレベルとして設定されます。
solution: Experience Cloud Services,Analytics
title: アプリのアクションの追跡
topic-fix: Developer and implementation
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
exl-id: ff317eff-1b8e-46e1-a305-a404979447cb
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---

# アプリのアクションの追跡 {#track-app-actions}

アクションは、アプリ内で発生し、測定対象となるイベントです。各アクションには、イベントが発生するたびに増分される、1 つ以上の対応する指標があります。例えば、記事が表示されるたび、またはレベルが完了するたびに、新規サブスクリプションを追跡します。これらのイベントに対応する指標は、サブスクリプション、読み取った記事、完了したレベルとして設定されます。

アクションは自動的には追跡されません。そのため、イベントを追跡するには、`trackAction` を呼び出す必要があります。

## アクションのトラッキング {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 追跡するアクションがアプリ内で発生したら、`trackAction` を呼び出して、このアクションのヒットを送信します。

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >この呼び出しをおこなうコードが、アプリがバックグラウンドになっているときに実行される可能性がある場合は、`trackActionFromBackground` ではなく `trackAction` を呼び出します。

1. Adobe Mobile Services UI で、アプリを選択し、「**[!UICONTROL アプリ設定]**」をクリックします。

1. 「**[!UICONTROL 変数と指標の設定]**」をクリックしてから、「**[!UICONTROL カスタム指標]**」タブをクリックします。

1. コードに定義されているコンテキストデータ名（例えば、`a.action=myapp.ActionName`）をカスタムイベントにマッピングします。

   ![](assets/map-event-context-data.png)

すべてのアクション値を保持する prop を設定することもできます。そのためには、「**[!UICONTROL カスタムアクション]**」などの名前のカスタム prop をマッピングし、値を `a.action` に設定します。

![](assets/map-custom-prop.png)

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

アクション名に加え、各 trackAction コールとともに追加のコンテキストデータを送信できます。

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

コンテキストデータ値は、カスタム変数にマッピングする必要があります。

![](assets/map-variable-context-action.png)

## バックグラウンドアクションの追跡 {#section_AC13013F207D4FBAAF27E4412034251E}

アプリがバックグラウンドになっているときに実行される可能性があるコードのアクションを追跡する場合は、`trackActionFromBackground` ではなく `trackAction` を呼び出します。`trackActionFromBackground` には、実行すべきではないときにライフサイクルコールを実行しないようにする、いくつかの追加ロジックが含まれています。

## アクションレポート {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| インターフェイス | レポート |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL アクションパス]**&#x200B;レポート。アプリでアクションが発生する順序を表示します。任意のレポートで「**[!UICONTROL カスタマイズ]**」をクリックすると、ランク付け、トレンド表示または分類レポートでアクションを表示したり、フィルターを適用して特定のセグメントのアクションを表示したりできます。 |
| Marketing Reports and Analytics | **[!UICONTROL カスタムイベント]**&#x200B;レポート。アクションがカスタムイベントにマップされた後、他のすべての Analytics イベントと同様にモバイルイベントを表示できます。 |
| アドホック分析 | **[!UICONTROL カスタムイベント]**&#x200B;レポート。アクションがカスタムイベントにマップされた後、他のすべての Analytics イベントと同様にモバイルイベントを表示できます。 |
