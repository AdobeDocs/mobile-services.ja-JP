---
description: ライフタイム値を使用して、各 Android ユーザーのライフタイム値を測定し、ターゲットを設定できます。この値を使用して、全期間の購入、広告ビュー、ビデオ完了、ソーシャル共有、写真のアップロードなどを保存できます。
seo-description: ライフタイム値を使用して、各 Android ユーザーのライフタイム値を測定し、ターゲットを設定できます。この値を使用して、全期間の購入、広告ビュー、ビデオ完了、ソーシャル共有、写真のアップロードなどを保存できます。
seo-title: 訪問者のライフタイム値
solution: Experience Cloud,Analytics
title: 訪問者のライフタイム値
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---


# 訪問者のライフタイム値 {#visitor-lifetime-value}

ライフタイム値を使用して、各 Android ユーザーのライフタイム値を測定し、ターゲットを設定できます。この値を使用して、全期間の購入、広告ビュー、ビデオ完了、ソーシャル共有、写真のアップロードなどを保存できます。

`trackLifetimeValueIncrease` で値を送信するたびに、その値が既存の値に追加されます。ライフタイム値はデバイス上に保存され、`lifetimeValue` を呼び出していつでも取得することができます。

## 訪問者のライフタイム値の追跡 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. 値の増分量を指定して `trackLifetimeValueIncrease` を呼び出します。

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## 追加データの送信 {#section_3EBE813E54A24F6FB669B2478B5661F9}

全期間値に加えて、各アクション追跡呼び出しで追加のコンテキストデータを送信することができます。

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

コンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-context-ltv.png)

