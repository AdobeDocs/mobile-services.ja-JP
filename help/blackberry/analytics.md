---
description: プロジェクトにライブラリを追加した後、アプリ内の任意の場所でAnalyticsメソッド呼び出しを行うことができます（必ずADBMobile.hをクラスに読み込んでください）。
seo-description: プロジェクトにライブラリを追加した後、アプリ内の任意の場所でAnalyticsメソッド呼び出しを行うことができます（必ずADBMobile.hをクラスに読み込んでください）。
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 5%

---


# Analytics {#analytics}

プロジェクトにライブラリを追加した後、アプリ内の任意の場所でAnalyticsメソッド呼び出しを行うことができます（必ずADBMobile.hをクラスに読み込んでください）。

## Analyticsでのモバイルアプリケーションレポートの有効化 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

コードを追加する前に、Analytics管理者に次の情報を入力して、モバイルアプリのライフサイクル追跡を有効にしてもらいます。 これにより、開発を開始する際に、レポートスイートで指標を取り込む準備が整います。


1. 管理ツール **[!UICONTROL /]** レポートスイートを開き **** 、モバイルレポートスイートを選択します。
1. 設定 **[!UICONTROL の編集]** / **[!UICONTROL モバイル管理]** / **[!UICONTROL モバイルアプリケーションレポート]**&#x200B;の順にクリックします。

   ![](assets/mobile-settings.png)

1. 「最新のアプリレポートを **[!UICONTROL 有効にする]**」をクリックします。

   必要に応じて、「モバイルロケーショントラッキングを **[!UICONTROL 有効にする]** 」をクリックし **[!UICONTROL 、バックグラウンドヒットに対して「従来のレポートとアトリビューションを]**&#x200B;有効にする」をクリックすることもできます。

   ![](assets/enable-lifecycle.png)

これで、ライフサイクル指標を取り込む準備が整い、モバイルアプリケーションレポートがマーケティングレポートインターフェイスの **[!UICONTROL レポート]** メニューに表示されます。

## ライフサイクル指標の収集 {#task_25D469C62DF84573AEB5E8E950B96205}

1. アプリでライフサイクル指標を収集するには、コンストラクター `collectLifecycleData()` を呼び出し `ApplicationUI` ます。

   以下に例を示します。

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   同じセッション `collectLifecycleData()` で2回呼び出された場合、最初の呼び出しの後に毎回クラッシュが報告されます。 SDKは、アプリケーションがシャットダウンされたときに、終了が成功したことを示すフラグを設定します。 このフラグが設定されていない場合は、クラッシュ `collectLifecyleData()` を報告します。

## event、prop、eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


ADBMobileクラスおよびメソッドリファレンスを参照している場合 [](/help/blackberry/methods.md)、イベント、eVar、prop、ヒーラーおよびリストを設定する場所をお考えの方は、おそらくお考えでしょう。 バージョン4では、これらのタイプの変数を直接アプリで割り当てることはできなくなりました。 代わりに、SDKは、コンテキストデータと処理ルールを使用して、レポート用にアプリデータをAnalytics変数にマッピングします。

処理ルールには、次のようないくつかの利点があります。

* データマッピングは、更新をApp Storeに送信しなくても変更できます。
* データには、レポートスイートに固有の変数を設定する代わりに、意味のある名前を付けることができます。
* 追加のデータを送信する場合、影響はほとんどありません。 これらの値は、処理ルールを使用してマッピングされるまで、レポートに表示されません。

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## 処理ルール {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

処理ルールは、コンテキストデータ変数で送信するデータをeVar、propおよびその他の変数にコピーしてレポートするために使用します。

[処理ルールトレーニング](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[処理ルール](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[処理ルールを使用するための承認の取得](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

論理的な順序を維持するのに役立つため、コンテキストデータ変数を「名前空間」を使用してグループ化することをお勧めします。 例えば、製品に関する情報を収集する場合、次の変数を定義できます。

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

コンテキストデータ変数は、処理ルールインターフェイスではアルファベット順に並べ替えられるので、名前空間を使用すると、同じ名前空間内の変数をすばやく確認できます。

また、evarまたはprop番号を使用してコンテキストデータキーに名前を付ける方もいらっしゃいます。

```js
"eVar1":"jimbo"
```

This might make it *slightly* easier when you perform the one time mapping in processing rules, but you lose readability during debugging and future code updates can be more difficult. 代わりに、キーと値にはわかりやすい名前を使用することを強くお勧めします。

```js
"username":"jimbo"
```

カウンターイベントを定義するコンテキスト変数は、同じキーと値を持つことができます。

```js
"logon":"logon"
```

増分イベントを定義するコンテキストデータ変数は、イベントをキーとして、増分量を値として持つことができます。

```js
"levels completed":"6"
```

>[!TIP]
>
>アドビは名前空間「`a.`」を予約します。この小さな制限に加えて、コンテキストデータ変数は、競合を回避するために、ログイン会社内で一意である必要があります。

## オフライン追跡を有効にする {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

デバイスがオフラインの場合にヒットを保存するには、 `ADBMobileConfig.json` ファイルでオフライン追跡をオプションで有効にすることができます。

オフライン追跡を有効にする前に、設定ファイルのリファレンスに記載されているタイムスタンプ要件に細心の注意を払ってください。

## Analytics メソッド

BlackBerryで使用できるAnalyticsメソッドのリストについては、『 *Adobeモバイルクラス* 』の「 [Analyticsメソッド」および『メソッドリファレンス』を参照してください](/help/blackberry/methods.md)。