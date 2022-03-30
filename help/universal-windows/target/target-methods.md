---
description: ユニバーサル Windows プラットフォームライブラリが提供する Target メソッドの一覧です。
solution: Experience Cloud Services,Analytics
title: Target メソッド
topic-fix: Developer and implementation
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
exl-id: d7aeee41-1c34-4f98-8455-e9f429287cfc
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 37%

---

# Target メソッド {#target-methods}

ユニバーサル Windows プラットフォームライブラリが提供する Target メソッドの一覧です。

SDK は現在、Analytics、Target、Audience Managerなど、複数のAdobe Experience Cloudソリューションをサポートしています。

[ライフサイクル指標](/help/universal-windows/metrics.md) は、各 mbox が読み込むパラメーターとして送信されます。

>[!TIP]
>
>消費時 `winmd` メソッドを winJS(JavaScript) から呼び出すと、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

## クラス参照：TargetLocationRequest

## プロパティ

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

   送信数 `request` を設定した Target サーバーに追加し、ブロックで生成されたオファーの文字列値を返します。 `callback`.

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest (winJS:createRequest)**

   を作成します。 `TargetLocationRequest` オブジェクトに指定したパラメーターを含めます。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS:createOrder ConfirmRequest&#x200B;)**

   を作成します。 `TargetLocationRequest` オブジェクトに指定したパラメーターを含めます。

   * このメソッドの構文を次に示します。

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies (winJS:clearCookies)**

   現在のデバイス上のアプリケーションの Target Cookie をクリアします。

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
      staticPlatform::String ^GetPcId();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId (winJS:getSessionId)**

   現在のデバイスのセッション ID Cookie を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```
