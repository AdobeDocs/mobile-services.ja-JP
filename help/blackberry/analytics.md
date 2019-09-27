---
description: プロジェクトにライブラリを追加した後は、アプリケーション内のどこでも任意の Analytics メソッドを呼び出せます（クラスに ADBMobile.h が読み込まれていることを確認してください）。
seo-description: プロジェクトにライブラリを追加した後は、アプリケーション内のどこでも任意の Analytics メソッドを呼び出せます（クラスに ADBMobile.h が読み込まれていることを確認してください）。
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

プロジェクトにライブラリを追加した後は、アプリケーション内のどこでも任意の Analytics メソッドを呼び出せます（クラスに ADBMobile.h が読み込まれていることを確認してください）。

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

コードを追加する前に、次の手順を完了してモバイルアプリケーションのライフサイクル追跡を有効にするよう Analytics 管理者に依頼してください。この手順を完了すると、開発を開始する際にレポートスイートで指標を収集できるようになります。


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## ライフサイクル指標の収集 {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   以下に例を示します。

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. アプリケーションがシャットダウンされると、正常終了を示すフラグが SDK によって設定されます。If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


『 [ADBMobileクラスとメソッドリファレンス』を参照している場合](/help/blackberry/methods.md)、イベント、eVar、prop、ヒア、リストを設定する場所が分からないかもしれません。 バージョン 4 では、これらの種類の変数をアプリケーション内で直接割り当てられなくなっています。代わりに、SDK は、コンテキストデータと処理ルールを使用して、レポート用にアプリデータを Analytics 変数にマップします。

処理ルールには次の利点があります。

* App Store に更新を提出することなく、データマッピングを変更することができます。
* レポートスイートに固有の変数を設定する代わりに、意味のある名前をデータに使用できます。
* 追加のデータの送信にはほとんど影響しません。これらの値は、処理ルールを使用してマップされるまではレポートに表示されません。

そのため、変数に直接代入していた値はすべて、`data` HashMap に追加する必要があります。

## 処理ルール {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。

[処理ルールのトレーニング](https://tv.adobe.com/embed/1181/16506/)（Summit 2013）

[処理ルール](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[処理ルールの使用を承認する](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

「名前空間」を使用してコンテキストデータ変数をグループ化することをお勧めします。これにより論理的な順序を維持できます。例えば、ある製品に関する情報を収集する場合、以下の変数を定義できます。

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

コンテキストデータ変数は、処理ルールインターフェイスでアルファベット順に並べ替えられます。そのため、名前空間を使用することで、同じ名前空間に属している変数がすぐにわかります。

また、コンテキストデータキーの名前に evar や prop の番号が使用されている場合もあるとの報告があります。

```js
"eVar1":"jimbo"
```

この命名方法を使用すると、処理ルールで 1 回限りのマッピングを実行するときの手間は若干減りますが、コードが読みにくくなるので、デバッグや将来のコード更新が困難になる可能性があります。**&#x200B;そのため、キーと値にはわかりやすい名前を付けることを強くお勧めします。

```js
"username":"jimbo"
```

カウンターイベントを定義するコンテキスト変数には、同じキーと値を設定できます。

```js
"logon":"logon"
```

増分イベントを定義するコンテキストデータ変数では、イベントをキーに、増分する量を値に設定することができます。

```js
"levels completed":"6"
```

>[!TIP]
>
>アドビは名前空間を予約しま `a.`す。 このわずかな制約以外で、競合を回避するために必要なのは、コンテキストデータ変数をログイン会社内で一意にすることだけです。

## オフライン追跡を有効にする {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

オフライン追跡を有効にする前に、設定ファイルのリファレンスで説明されているタイムスタンプの要件に十分注意してください。

## Analyticsメソッド

BlackBerryで使用できるAnalyticsメソッドの一覧については、 *Adobe mobileクラスの* Analyticsメソッドおよびメソッドリ [ファレンスを参照してください](/help/blackberry/methods.md)。