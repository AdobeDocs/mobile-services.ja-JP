---
description: 様々な変数および指標を設定することで、アプリから受け取ったデータを追跡および管理できます。
keywords: モバイル
seo-description: 様々な変数および指標を設定することで、アプリから受け取ったデータを追跡および管理できます。
seo-title: アプリの管理
solution: Marketing Cloud,Analytics
title: アプリの管理
topic: 指標
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# アプリの管理 {#managing-your-app}

様々な変数および指標を設定することで、アプリから受け取ったデータを追跡および管理できます。

## 変数と指標の設定 {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **標準変数および指標**

   各アプリには、買い物かごおよび購入アクティビティを追跡するための変数および指標が含まれます。Some purchase information cannot be handled with processing rules, so the SDK exposes the special `"&&products"` context data. 例えば、買い物かごへの追加、買い物かごからの削除、チェックアウト、注文などの変数を持つことができます。コンテキストデータは、Adobe Analytics のデータにマッピングされる必要があります。この変数がコンテキストデータからの単純なマッピングで設定される場合、マッピングのためのキーになります。変数にAnalytics管理ツールのより複雑なルールが入力される場合は、空白のままにします。

   これらの変数および指標について詳しくは、次を参照してください。

   * [Androidの製品変数](/help/android/analytics-main/products/products.md)
   * [iOSでの製品変数](/help/ios/analytics-main/products/products.md)

* **カスタム変数**

   カスタム変数ページには、アプリデータを含むレポートスイート用に設定されたすべてのカスタム Analytics 変数が表示されます。また、追加の変数を有効にしたり、コンテキストデータを Analytics 変数にマッピングすることもできます。

### コンテキストデータの Analytics 変数へのマッピング

Click **[!UICONTROL Manage App Settings]** &gt; **[!UICONTROL Manage Variables &amp; Metrics]** &gt; **[!UICONTROL Custom Variables]**.

These mappings call the same API that is used in [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![コンテキストデータマッピング](assets/custom_data_content.png)

次に、設定できるカスタム変数のリストを示します。

* The **[!UICONTROL Custom Properties]** (or props) answer the question "which one?" prop は、同じヒットに送信された別の変数および指標に関連付けられるテキスト値に設定できます。値は、レポートのフィルターに使用したり、関連する指標によるランク順でリストすることができます。

   トラッキングコール（またはヒット）のプロパティに設定した値は、そのコールにのみ適用されます。

* The **[!UICONTROL Custom Variables]** (or evars) also answer the question "which one?" ただし、値の有効期限が切れるか新しい値が設定されるまで、eVar の値は送信されたヒットだけでなく、後続のヒットで送信された変数と指標にも適用できます。
* The **[!UICONTROL Custom List Variables (or Multi-Value Variables)]** behave the same as variables except they allow you to capture multiple values on one hit. For more information, see [List Variables](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html).

Analyticsでは、以下のマッピングがMobile Servicesで作成されたものとして表示されます。

* **[!UICONTROL 名前]**

   データ収集変数のわかりやすい名前。

* **[!UICONTROL コンテキストデータ]**

   この変数がコンテキストデータからの単純なマッピングで設定される場合、マッピングのためのキーになります。変数が Analytics の管理ツールのより複雑なルールによって設定されている場合、このフィールドを空のままにします。

   コンテキストデータ列をクリックして、マッピングするコンテキストデータ変数を選択します。ドロップダウンリストには、過去 30 日間に値を受け取った変数名が表示されています。マッピングするコンテキストデータがリストにない場合は、直接入力できます。

* **[!UICONTROL 永続性（カスタム変数とカスタムリスト変数）]**

   永続性は、カスタム変数（eVar）の値の有効期限が切れる時期、または追加のヒットと関連付けられなくなる時期を決定します。ヒットが実行される際に eVar の有効期限が切れていると、値「なし」がその eVar のヒットに関連付けられます。これは、ヒットが実行された際にアクティブな eVar の値がないことを意味します。

   次のいずれかのオプションを選択できます。

   * **[!UICONTROL セッション]**

      eVar値は、Analytics訪問の間保持されます。

   * **[!UICONTROL コールのみ]**

      The eVar value persists only for the tracking call or hit it in which it was included.

   * **[!UICONTROL 無期限]**

      このeVar値は、以降のすべてのトラッキングコールで維持されます。
   * **[!UICONTROL アドバンス]**

      Adobe Analytics には、eVar の永続性を設定するための、より高度な UI が備わっています。If a persistence value is set for the eVar that is not supported in Mobile Services, this value is displayed in the Mobile Services UI.

      To manage eVars, click **[!UICONTROL Adobe Analytics Report Suite Manager]** &gt; **[!UICONTROL Conversion Variables UI]**.

   * **[!UICONTROL リストのサポート]**

      1回のトラッキングコールでプロパティに関連付ける複数の値を渡すことができます。 区切り文字は1文字にする必要があり、ゼロまたはスペースは使用できません。

   * **[!UICONTROL Delimiter]**

      区切り文字は1文字にする必要があり、ゼロまたはスペースは使用できません。

### 追加の Analytics 変数

各変数セクションの下部にあるドロップダウンリストを使用して、追加の変数を有効化できます。

![変数の追加](assets/add_variable.png)

未使用の変数番号を選択して、名前を入力します。オプションで、保存したいコンテキストデータ変数およびその他の情報を指定できます。

* **カスタム指標**

   *指標（またはイベント）は、質問に対する答えをどれ*&#x200B;だけ得ますか。何 *人？*&#x200B;をインストールします。イベントは、ユーザーが行動を起こすたびに増分したり、価格などの数値を保持したりできます。カスタム指標には、アプリが作成された、PDF または CSV ファイルがダウンロードまたは書き出された、キャンペーンが保存された、SDK がダウンロードされた、レポートが実行された、アプリストアへのリンクが追加された、アプリ内メッセージがアクティブ化された、などのイベントが含まれます。

   次のカスタム指標タイプのいずれかを選択します。

   * **[!UICONTROL 整数]**
   * **[!UICONTROL 小数]**
   * **[!UICONTROL 通貨]**

## 目標地点の設定 {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

目標地点を使用すると、地理的な場所を定義できます。これらの場所は、相関関係の設定や、アプリ内メッセージでのターゲット設定などに使用できます。 ヒットが目標地点内で送信されると、その目標地点がヒットに追加されます。目標地点について詳しくは、[目標地点の設定](/help/using/location/t-manage-points.md)を参照してください。

## リンク先を管理 {#section_F722A387E22A430187B063D358A87711}

リンク先を作成、編集、アーカイブ／アーカイブ解除および削除できます。これらの宛先は、マーケティングリンク、プッシュ通知またはアプリ内メッセージの作成時にインラインで呼び出すことができます。 For more information about link destinations, see Manage Link Destinations.[](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md)

## ポストバックを管理 {#section_78B0A8D7AE6940E78D85AE3AB829E860}

ポストバックを使用すると、Adobe Mobile によって収集されたデータを別のサードパーティサーバーに送信できます。アプリ内メッセージを表示するために設定するのと同じ条件を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように Mobile を設定できます。ポストバックについて詳しくは、[ポストバックの設定](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md)を参照してください。
