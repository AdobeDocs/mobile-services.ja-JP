---
description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-title: 時間指定アクション
solution: Marketing Cloud、Analytics
title: 時間指定アクション
topic: 開発者と導入
uuid: dbcbac5a-6345-49f6- b050-0db05292f005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。

時間計測アクションに対しては、以下の指標がレポートされます。

* アプリの開始から終了までの合計秒数 - 複数のセッションにまたがって計測
* 開始から終了までの合計秒数（クロックタイム）

オプションのコールバックを使用すると、時間計測アクションの完了時に追加のアクションを実行できます。

* コードを実行して何らかのロジック（計測された時間に基づくオプションのカスタムロジック）を追加します。
* 時間として渡す前にコンテキストデータを追加します。
* まだ送信されていないヒットと時間をキャンセルします。

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
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

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

時間計測アクション名に加え、アクション開始コールおよびアクション更新コールとともに追加のコンテキストデータを送信できます。

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

コンテキストデータ値は、カスタム変数にマップする必要があります。

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

