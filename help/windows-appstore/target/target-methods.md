---
description: Windows8.1ユニバーサルアプリストアライブラリによって提供されるTargetメソッドのリストです。
seo-description: Windows8.1ユニバーサルアプリストアライブラリによって提供されるTargetメソッドのリストです。
seo-title: Target メソッド
solution: Marketing Cloud、Analytics
title: Target メソッド
topic: 開発者と導入
uuid: 8c35b31c- c70b-4dba-8759-173342a301e9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target メソッド {#target-methods}

Windows8.1ユニバーサルアプリストアライブラリによって提供されるTargetメソッドのリストです。

現在、SDK では、Analytics、Target、Audience Manager をはじめとする複数の Adobe Experience Cloud ソリューションがサポートさています。これらのメソッドには、ソリューションに応じたプレフィックスが付けられています。Target メソッドには「Target」というプレフィックスが付けられています。

[ライフサイクル指標](/help/windows-appstore/metrics.md)は、各 mbox が読み込むパラメーターとして送信されます。

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## クラスリファレンス:targetLocationRequest

### プロパティ

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## 文字列定数

この情報は、カスタムパラメーターのキーを設定するのに役立ちます。

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

* **loadRequest（WinJS:loadRequest）**

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

* **CreateRequest（WinJS:CreateRequest）**

   指定されたパラメーターで `TargetLocationRequest` オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrderConfirmRequest（WinJS:CreateOrderConfirmRequest）**

   指定されたパラメーターで `TargetLocationRequest` オブジェクトを作成します。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies（WinJS:ClearCookies）**

   現在のデバイス上にあるアプリケーションの Target Cookie をクリアします。

   * このメソッドの構文を次に示します。

      ```csharp
      static void ClearCookies(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **getPCId（winJS:getPCId）**

   現在のデバイスの PC ID Cookie を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **getSessionId（winJS:getSessionId）**

   現在のデバイスのセッション ID Cookie を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

