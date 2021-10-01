---
description: Windows 8.1 ユニバーサルアプリストアライブラリが提供する Target メソッドの一覧です。
solution: Experience Cloud,Analytics
title: Target メソッド
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Target メソッド {#target-methods}

Windows 8.1 ユニバーサルアプリストアライブラリが提供する Target メソッドの一覧です。

SDK は現在、Analytics、Target、Audience Managerを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Analytics メソッドの場合、プレフィックスは「Target」です。

[ライフサイクル指標](/help/windows-appstore/metrics.md)は、各 mbox が読み込むパラメーターとして送信されます。

>[!TIP]
>
>winJS(JavaScript) の `winmd` メソッドを使用すると、すべてのメソッドの最初の文字が自動的に小文字に変換されます。

## クラス参照：TargetLocationRequest

### プロパティ

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 文字列定数

この情報は、カスタムパラメーターのキーを設定する場合に役立ちます。

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest (winJS:loadRequest)**

   設定した Target サーバーに `request` を送信し、ブロック `callback` で生成されたオファーの文字列値を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest (winJS:createRequest)**

   指定されたパラメータで `TargetLocationRequest` オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS:createOrder &#x200B; ConfirmRequest)**

   指定されたパラメータで `TargetLocationRequest` オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS:clearCookies)**

   現在のデバイス上のアプリケーションの Target の Cookie をクリアします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void ClearCookies(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS:getPcId)**

   現在のデバイスの PC ID Cookie を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS:getSessionId)**

   現在のデバイスのセッション ID Cookie を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
