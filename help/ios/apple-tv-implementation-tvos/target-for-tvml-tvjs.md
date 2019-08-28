---
description: .xml ファイルと直接置き換えることによって、TVML／TVJS アプリで Adobe Target を利用できます。カスタムの ADBTarget XML 要素を使用して、Target コンテンツで置き換えるページのエリアを指定します。
seo-description: .xml ファイルと直接置き換えることによって、TVML／TVJS アプリで Adobe Target を利用できます。カスタムの ADBTarget XML 要素を使用して、Target コンテンツで置き換えるページのエリアを指定します。
seo-title: TVML／TVJS 対応の Adobe Target
title: TVML／TVJS 対応の Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# TVML／TVJS 対応の Adobe Target{#adobe-target-for-tvml-tvjs}

.xml ファイルと直接置き換えることによって、TVML／TVJS アプリで Adobe Target を利用できます。カスタムの ADBTarget XML 要素を使用して、Target コンテンツで置き換えるページのエリアを指定します。

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. 詳しくは、tvOSを使用した [Apple TV実装](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)を参照してください。

## はじめに {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>置き換えたいものを計画する必要があります。

ユースケースには、ラベルの文字列値を置き換えるくらいシンプルなものもあれば、ページ全体を置き換えるくらい複雑なものもあります。

## ADBTarget要素の設定 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

`ADBTarget` 要素内で、`mbox` プロパティに Mbox 名を指定する必要があります。You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Mbox ロケーション名.

   * プロパティタイプ:文字列
   * このプロパティは必須です。

* **`id`**

   注文ID。

   * プロパティタイプ:文字列
   * このプロパティは必須 **で** はありません。

* **`total`**

   注文の合計。

   * プロパティタイプ:文字列
   * このプロパティは必須 **で** はありません。

* **`purchasedProductIds`**

   この注文で購入する製品の ID のコンマ区切りリスト。

   * 以下に、このプロパティのコードサンプルを示します。


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * プロパティタイプ:文字列
   * このプロパティは必須 **で** はありません。

* **`mboxParameters`**

   `mboxParameters` のキーと値のペアのリスト。この文字列内の各エントリはセミコロンで区切られ、キー値はコロンで区切られます。

   * 以下に、このプロパティのコードサンプルを示します。

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * プロパティタイプ:文字列
   * このプロパティは必須 **で** はありません。

* **`customParameterName`**

   このプロパティの値 `customParameterValue`は、です。

   * プロパティタイプ:文字列
   * このプロパティは必須 **で** はありません。


## 例 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 例 1

以下の例では、`ADBTarget` ページ内で `LandingPage.xml.js` 要素を使用して、アラートのコンテンツを置き換えています。

#### Target の設定

`landingPage` という名前の Mbox ロケーションがあり、オファーコンテンツが次のように設定されているとします。

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### landingPage.xml.js の設定

* landingPage.xml.js の設定を以下に示します。

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Target へのリクエストが成功し、オファーコンテンツが返された場合、ページは次のようになります。

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Target サーバーに到達できなかったり、リクエストがタイムアウトした場合、ページは次のようになります。

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### 例 2

以下の例は、カスタムデータを `ADBTarget` 要素に追加する方法を説明したものです。このメソッドを使用して、Target のこの Mbox ロケーションに対して、条件付きエクスペリエンスとオファーコンテンツを作成できます。

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
