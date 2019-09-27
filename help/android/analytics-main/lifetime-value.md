---
description: ライフタイム値を使用すると、各 Android ユーザーの全期間値を測定し、ターゲットにすることができます。この値は、全期間の購入、広告ビュー、ビデオ完了、ソーシャルシェア、写真のアップロードなどを保存するために使用できます。
seo-description: ライフタイム値を使用すると、各 Android ユーザーの全期間値を測定し、ターゲットにすることができます。この値は、全期間の購入、広告ビュー、ビデオ完了、ソーシャルシェア、写真のアップロードなどを保存するために使用できます。
seo-title: 訪問者のライフタイム値
solution: Marketing Cloud,Analytics
title: 訪問者のライフタイム値
topic: 開発者と導入
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Visitor lifetime value {#visitor-lifetime-value}

ライフタイム値を使用すると、各 Android ユーザーの全期間値を測定し、ターゲットにすることができます。この値は、全期間の購入、広告ビュー、ビデオ完了、ソーシャルシェア、写真のアップロードなどを保存するために使用できます。

`trackLifetimeValueIncrease` で値を送信するたびに、その値が既存の値に追加されます。ライフタイム値はデバイス上に保存され、`lifetimeValue` を呼び出していつでも取得することができます。

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. [ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、 *Core実装およびライフサイクルのIntelliJ IDEAまたはEclipse ProjectへのSDKと設定ファイルの追加*[を参照してください](/help/android/getting-started/dev-qs.md)。
1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. 値の増分量を指定して `trackLifetimeValueIncrease` を呼び出します。

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

全期間値に加えて、各アクション追跡呼び出しで追加のコンテキストデータを送信することができます。

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

コンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-ltv.png)

