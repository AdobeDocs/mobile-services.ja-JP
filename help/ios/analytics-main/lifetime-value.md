---
description: ライフタイム値を使用して、各ユーザーのライフタイム値を測定し、ターゲットを設定できます。
seo-description: ライフタイム値を使用して、各ユーザーのライフタイム値を測定し、ターゲットを設定できます。
seo-title: 訪問者のライフタイム値
solution: Marketing Cloud、Analytics
title: 訪問者のライフタイム値
topic: 開発者と導入
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

ライフタイム値を使用して、各ユーザーのライフタイム値を測定し、ターゲットを設定できます。

`trackLifetimeValueIncrease` で値を送信するたびに、その値が既存の値に追加されます。ライフタイム値はデバイス上に保存され、`lifetimeValue` を呼び出していつでも取得することができます。この値を使用して、全期間の購入、広告ビュー、ビデオ完了、ソーシャル共有、写真のアップロードなどを保存できます。

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、コア実装および *ライフサイクル* で [プロジェクトにSDKおよび設定ファイルを追加を参照](/help/ios/getting-started/dev-qs.md)してください。
1. ライブラリをインポートします。

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. 値の増分量を指定して `trackLifetimeValueIncrease` を呼び出します。

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

ライフタイム値に加え、各 trackAction コールとともに追加のコンテキストデータを送信できます。

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

コンテキストデータ値は、カスタム変数にマップする必要があります。

![](assets/map-variable-context-ltv.png)

