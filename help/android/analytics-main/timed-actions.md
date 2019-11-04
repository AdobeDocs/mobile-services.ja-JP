---
description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-description: 時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。
seo-title: 時間計測アクション
solution: Experience Cloud,Analytics
title: 時間計測アクション
topic: 開発者と導入
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: ht
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

---


# 時間計測アクション {#timed-actions}

時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。SDK は、アクションが完了するまでにかかる各セッションの時間と全セッションの合計時間を計算します。時間計測アクションを使用して、セグメントを定義し、購入までの時間、パスレベル、チェックアウトフローなどを比較することができます。

時間計測アクションでは、次の指標がレポートされます。

* （全セッションの）開始から終了までのアプリ内の合計秒数
* 開始から終了までの合計秒数（クロックタイム）

オプションのコールバックを使用すると、時間計測アクションの完了時に追加のアクションを実行できます。

* コードを実行して何らかのロジック（計測された時間に基づくオプションのカスタムロジック）を追加します。
* 時間を渡す前にコンテキストデータを追加します。
* まだ送信されていないヒットと時間をキャンセルします。

## 時間計測アクションの追跡 {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. `trackTimedActionStart` を呼び出し、時間計測アクション名とオプションのコンテキストデータを指定します。

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. （オプション）いつでも、時間計測アクション名を使用して `trackTimedActionUpdate` を呼び出し、その他のコンテキストデータを追加することができます。

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. イベントが完了したら、`trackTimedActionEnd` を呼び出し、時間計測アクション名と、すべてのデータを検索して時間を計算する `TimedActionBlock`（コールバック）を渡します。

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   経過時間イベント指標は、自動レポート作成のためにモバイルソリューション変数に保存されます。

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

時間計測アクション名に加えて、アクション開始およびアクション更新呼び出しで追加のコンテキストデータを送信することもできます。

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

コンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-ltv.png)

## 例 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```

