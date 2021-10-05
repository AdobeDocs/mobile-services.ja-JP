---
description: プロジェクトにライブラリを追加した後、アプリケーションの任意の場所で任意の Analytics メソッドを呼び出すことができます。
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
exl-id: cc96a7dd-ccc4-4914-8243-f3f160b75c21
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 19%

---

# Analytics {#analytics}

プロジェクトにライブラリを追加した後、アプリケーションの任意の場所で任意の Analytics メソッドを呼び出すことができます。

>[!TIP]
>
>必ず `ADBMobile.h` をクラスに読み込んでください。

## Analytics でのモバイルアプリレポートの有効化 {#section_F2F9234009184F20BA36B5CDE872B424}

コードを追加する前に、Analytics 管理者に次の手順を完了させて、モバイルアプリのライフサイクル追跡を有効にしてもらいます。 これにより、開発を開始する際に、レポートスイートで指標をキャプチャする準備が整います。

1. **[!UICONTROL 管理ツール]** / **[!UICONTROL レポートスイート]** を開き、モバイルレポートスイートを選択します。

1. **[!UICONTROL 設定を編集]** / **[!UICONTROL モバイル管理]** / **[!UICONTROL モバイルアプリケーションレポート]** をクリックします。

   ![モバイル設定](assets/mobile-settings.png)

1. 「**[!UICONTROL 最新のアプリレポートを有効にする]**」をクリックします。

   オプションで、「**[!UICONTROL モバイルロケーションの追跡を有効にする]**」または「**[!UICONTROL バックグラウンドヒットの従来のレポートと属性を有効にする]**」をクリックすることもできます。

   ![ライフサイクルの有効化](assets/enable-lifecycle.png)

これで、ライフサイクル指標を取り込む準備が整い、モバイルアプリケーションレポートがマーケティングレポートインターフェイスの **[!UICONTROL レポート]** メニューに表示されます。

### 新しいバージョン

定期的に、新しいバージョンのモバイルアプリケーションレポートがリリースされています。 新しいバージョンはレポートスイートに自動的に適用されないので、アップグレードを実行するには、これらの手順を繰り返す必要があります。 アプリに新しいExperience Cloud機能を追加するたびに、これらの手順を繰り返して最新の設定を使用することをお勧めします。

## ライフサイクル指標 {#section_532702562A7A43809407C9A2CBA80E1E}

アプリでライフサイクル指標を収集するには、次の例に示すように、アプリケーションがアクティブ化されたときにへの呼び出しを追加します。

### default.js の WinJS

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
};
```

### App.xaml.cs の C#

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### App.xaml.cpp 内の C++/CX

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

同じセッションで `CollectLifecycleData()` が 2 回呼び出された場合、最初の呼び出しのたびにアプリケーションからクラッシュが報告されます。 アプリケーションがシャットダウンされると、SDK は終了が成功したことを示すフラグを設定します。 このフラグが設定されていない場合、`CollectLifecyleData()` はクラッシュを報告します。

## event、prop、eVar  {#section_76EA6F5611184C5CAE6E62956D84D7B6}

[SDK メソッド ](/help/universal-windows/c-configuration/methods.md) を見た場合は、イベント、eVar、prop、heir、リストを設定する場所を疑問に思うでしょう。 バージョン 4 では、これらのタイプの変数を直接アプリに割り当てることができなくなりました。 代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数へとマッピングします。

処理ルールには、次のようないくつかの利点があります。

* アプリストアにアップデートを送信しなくてもデータマッピングを変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信しても、影響はほとんどありません。これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

変数に直接割り当てていた値は、代わりにコンテキストデータに追加する必要があります。

## 処理ルール {#section_66EE762EEA5E4728864166201617DEBF}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar、prop およびその他の変数にコピーするために使用します。

[処理ルールヘルプ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Adobeでは、論理的な順序を維持するのに役立つ「名前空間」を使用してコンテキストデータ変数をグループ化することをお勧めします。 例えば、製品に関する情報を収集する場合、次の変数を定義できます。

```javascript
"product.type":"hat";
"product.team":"mariners";
"product.color":"blue";
```

コンテキストデータ変数は、処理ルールインターフェイスでアルファベット順に並べ替えられるので、名前空間を使用すると、同じ名前空間にある変数をすばやく確認できます。

また、eVarや prop 番号を使用してコンテキストデータキーに名前を付ける方もいると聞きました。

```js
"eVar1":"jimbo";
```

これにより、処理ルールで 1 回限りのマッピングを実行すると *少し* の方が簡単になりますが、コードが読みにくくなるので、デバッグや将来のコード更新が困難になる可能性があります。 代わりに、キーと値にはわかりやすい名前を使用することを強くお勧めします。

```js
"username":"jimbo";
```

カウンターイベントを定義するコンテキスト変数を「1」の値に設定します。

```js
"logon":"1";
```

増分イベントを定義するコンテキストデータ変数には、増分する値を設定できます。

```js
"levels completed":"6";
```

>[!TIP]
>
>アドビは名前空間「`a.`」を予約します。この制限以外は、競合を回避するために、コンテキストデータ変数はログイン会社内で一意である必要があります。

## products 変数 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

モバイル SDK で *`products`* を設定するには、特殊な構文を使用する必要があります。 詳しくは、[products 変数 ](/help/universal-windows/analytics/products.md) を参照してください。

## （オプション）オフライン追跡を有効にする {#section_955B2A03EB854742BDFC4A0A3C287009}

デバイスがオフラインの場合にヒットを保存するには、[SDK メソッド ](/help/universal-windows/c-configuration/methods.md) ファイルでオフライン追跡を有効にします。 オフライン追跡を有効にする前に、設定ファイルのリファレンスで説明されているタイムスタンプ要件に十分注意してください。

## 位置情報と目標地点 {#section_BAD34A8DD013454DB355121316BD7FD4}

位置情報を使用すると、位置データ（緯度/経度）および事前に定義された目標地点を測定できます。 `TrackLocation` 呼び出しごとに、次の情報が送信されます。

* 緯度/経度および POI（`ADBMobileConfig.json` 設定ファイルで定義された POI 内の場合）。

   これらは、自動レポート用にモバイルソリューション変数に渡されます。

* 中心からの距離と、コンテキストデータとして渡される精度。

   処理ルールを使用してキャプチャします。

位置を追跡するには：

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

`ADBMobileConfig.json` 設定ファイルで次の POI が定義されている場合：

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

デバイスの位置が定義した点から 7000 メートルの半径内にあると判断された場合、値 `San Francisco` を持つ `a.loc.poi` コンテキストデータ変数が `TrackLocation` ヒットと共に送信されます。 `a.loc.dist` コンテキスト変数が、定義された座標からの距離（メートル単位）と共に送信されます。

## ライフタイム値 {#section_D2C6971545BA4D639FBE07F13EF08895}

ライフタイム値を使用して、各ユーザーのライフタイム値を測定し、ターゲットを設定できます。`TrackLifetimeValueIncrease` で値を送信するたびに、その値が既存の値に追加されます。ライフタイム値はデバイス上に保存され、`GetLifetimeValue` を呼び出していつでも取得することができます。この値を使用して、全期間の購入、広告ビュー、ビデオ完了、ソーシャル共有、写真のアップロードなどを保存できます。

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## 時間計測アクション {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

時間計測アクションを使用すると、アクションの開始から終了までのアプリ内時間と合計時間を測定できます。 SDK は、セッションの時間と、アクションが完了するまでにかかる合計時間（セッション間）を計算します。 これを使用して、購入までの時間、パスレベル、チェックアウトフローなどを比較するセグメントを定義できます。

* 開始から終了までのアプリ内の合計秒数 - クロスセッション
* 開始から終了までの合計秒数（時刻）

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
