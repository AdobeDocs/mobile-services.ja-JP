---
description: .xmlファイルを直接置き換えることで、TVML/TVJSアプリでAdobe Targetを活用できます。 カスタムのADBTarget XML要素を使用して、ターゲットコンテンツに置き換えるページ領域を指定します。
seo-description: .xmlファイルを直接置き換えることで、TVML/TVJSアプリでAdobe Targetを活用できます。 カスタムのADBTarget XML要素を使用して、ターゲットコンテンツに置き換えるページ領域を指定します。
seo-title: TVML／TVJS 対応の Adobe Target
title: TVML／TVJS 対応の Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 70%

---


# TVML／TVJS 対応の Adobe Target{#adobe-target-for-tvml-tvjs}

.xmlファイルを直接置き換えることで、TVML/TVJSアプリでAdobe Targetを活用できます。 カスタムのADBTarget XML要素を使用して、ターゲットコンテンツに置き換えるページ領域を指定します。

>[!IMPORTANT]
>
>TVML ページで `ADBTarget` 要素を使用する前に、tvOS SDK を使用するように TVML／TVJS アプリを設定する必要があります。詳しくは、「[tvOS を使用した Apple TV 実装](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)」を参照してください。

## はじめに {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Target ロケーションを使用する `.xml` ファイルを特定します。
1. `ADBTarget` 要素を `<document>` 要素の子としてファイルに追加します。
1. Target が Mbox ロケーションを見つけられなかったり、タイムアウトした場合は、`<ADBTarget>` タグと `</ADBTarget>` タグの間の値がデフォルトコンテンツとして使用されます。

## Target の Mbox の設定 {#section_F2DA140C34B0421D976046F825B23123}

Target から返されたコンテンツで、`<ADBTarget>` と `</ADBTarget>` の間のすべてのコンテンツ（両方の `ADBTarget` タグを含む）を置き換えます。

>[!TIP]
>
>何を置き換えるかを適切に計画する必要があります。

ユースケースには、ラベルの文字列値を置き換えるくらいシンプルなものもあれば、ページ全体を置き換えるくらい複雑なものもあります。

## ADBTarget 要素の設定 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

`ADBTarget` 要素内で、`mbox` プロパティに Mbox 名を指定する必要があります。オプションで、カスタムプロパティを `customParameterName="customParameterValue"` 形式でリクエストに追加できます。

* **`mbox`**

   Mbox ロケーション名。

   * プロパティタイプ：文字列
   * このプロパティが必要です。

* **`id`**

   注文 ID。

   * プロパティタイプ：文字列
   * このプロパティは必須では&#x200B;**ありません**。

* **`total`**

   注文の合計。

   * プロパティタイプ：文字列
   * このプロパティは必須では&#x200B;**ありません**。

* **`purchasedProductIds`**

   この注文で購入する製品の ID のコンマ区切りリスト。

   * このプロパティのコードサンプルを次に示します。


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * プロパティタイプ：文字列
   * このプロパティは必須では&#x200B;**ありません**。

* **`mboxParameters`**

   `mboxParameters` のキーと値のペアのリスト。この文字列の各エントリはセミコロンで区切り、キーと値はコロンで区切ります。

   * このプロパティのコードサンプルを次に示します。

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * プロパティタイプ：文字列
   * このプロパティは必須では&#x200B;**ありません**。

* **`customParameterName`**

   このプロパティの値は `customParameterValue` です。

   * プロパティタイプ：文字列
   * このプロパティは必須では&#x200B;**ありません**。


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

* landingPage.xml.jsの設定を次に示します。

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* ターゲットへのリクエストが成功し、オファーのコンテンツが返された場合、ページの結果は次のようになります。

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* ターゲットサーバーに到達できない場合、または要求がタイムアウトした場合、ページは次の結果になります。

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
