---
description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、各セッションの時間と、アクションが完了するまでにかかる、セッションをまたいだ合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、各セッションの時間と、アクションが完了するまでにかかる、セッションをまたいだ合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-title: 時間計測アクション
solution: Experience Cloud,Analytics
title: 時間計測アクション
topic: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '403'
ht-degree: 100%

---


# 時間計測アクション {#timed-actions}

時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、各セッションの時間と、アクションが完了するまでにかかる、セッションをまたいだ合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。

時間計測アクションでは、次の指標がレポートされます。

* 開始から終了までのアプリ内の合計秒数 - クロスセッション
* 開始から終了までの合計秒数（時刻）

オプションのコールバックを使用すると、時間計測が完了した場合に、次の追加のアクションを実行できます。

* コードを実行し、期間の結果に基づく任意のカスタムロジックを追加する。
* 期間を渡す前にコンテキストデータを追加する。
* まだ送信されていないヒットと期間をキャンセルする。

## 時間計測アクションの追跡 {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```objective-c
   #import "ADBMobile.h"
   ```

1. `trackTimedActionStart` を呼び出し、時間計測アクション名とオプションのコンテキストデータを指定します。

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. （オプション）任意のタイミングでコンテキストデータを追加する場合は、時間計測アクション名を指定して `trackTimedActionUpdate` を呼び出します。

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. イベントが完了したら、`trackTimedActionEnd` を呼び出し、時間計測アクション名と、すべてのデータを検索して時間を計算する `TimedActionBlock`（コールバック）を渡します。

   経過時間イベント指標は、自動レポート作成のためにモバイルソリューション変数に保存されます。

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

時間計測アクション名に加え、アクション開始コールおよびアクション更新コールとともに追加のコンテキストデータを送信できます。

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

コンテキストデータ値は、カスタム変数にマッピングする必要があります。

![](assets/map-variable-context-ltv.png)

## 例 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

