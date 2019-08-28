---
description: 表示、トリガーおよび特徴オプションを含む、アプリ内メッセージのオーディエンスオプションを設定できます。
keywords: モバイル
seo-description: 表示、トリガーおよび特徴オプションを含む、アプリ内メッセージのオーディエンスオプションを設定できます。
seo-title: オーディエンス内メッセージ
solution: Marketing Cloud、Analytics
title: オーディエンス内メッセージ
topic: 指標
uuid: 6c815d4c-7626-4cf4-9158-3f059c79317a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

表示、トリガーおよび特徴オプションを含む、アプリ内メッセージのオーディエンスオプションを設定できます。

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. オーディエンスページで、次のフィールドに情報を入力します。

   * **[!UICONTROL View]**

      メッセージの表示をトリガーするオプションを選択します。

      * **[!UICONTROL 常に]**

         このオプションは、トリガーが発生するたびにメッセージが表示されることを意味します。

      * **[!UICONTROL 1 回]**

         このオプションは、初めてトリガーが発生したときだけメッセージが表示されることを意味します。

      * **[!UICONTROL クリックスルーまで]**

         このオプションは、ユーザーがクリックスルーするまで、トリガーが発生するたびにメッセージが表示されることを意味します。このトリガーは、フルスクリーンおよびアラートメッセージに適用されます。ほとんどのメッセージは、リダイレクトが必要であるか、またはインターネットからのリソースを使用するので、オフラインの場合に表示されません。ネットワーク接続に関係なく常にメッセージを表示するには、「**[!UICONTROL オフラインを表示]」チェックボックスを選択します。**
   * **[!UICONTROL トリガー]**

      ドロップダウンリストからオプションを選択して、条件を選択します。例えば、最初のドロップダウンリストで「**[!UICONTROL 起動済み]**」を選択し、2 番目のドロップダウンリストで「**存在する]」を選択します。[!UICONTROL **&#x200B;トリガー条件に適合し、メッセージを表示するヒットに含まれている必要があるカスタムのコンテキストデータを指定することもできます。

      >[!IMPORTANT]
      >
      >複数のトリガーを選択した場合、メッセージを表示するには、すべてのトリガーが同じヒットで発生する必要があります。

   * **[!UICONTROL 特性]**&#x200B;アプリ内メッセージがトリガーされたときにどのユーザーに表示されるかを決定し、指定したデータを持つヒットにオーディエンスをフィルター（セグメント化）することができます。例えば、目標地点にデンバーが含まれるというルールを定義できます。このフィルターを使用すると、トリガーの時点で目標地点のいずれかの名前に「デンバー」が含まれている顧客にメッセージを表示できます。



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>トリガーと特性は、アプリからAnalyticsに渡されるデータを使用します。値はコンテキストデータ、マップされた変数、および指標として渡されます。変数はテキストベースの値であり、指標は数値です。

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL 標準変数および指標]**
* **[!UICONTROL カスタム変数]**
* **[!UICONTROL カスタム指標]**

マッピングを検証したら、適切に一致するものまたは論理演算子を選択してメッセージのオーディエンスを設定します。

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![トリガーオプション](assets/custom_trigger_matcher_options.png)

次のシナリオでは、トリガーとして指標を選択するか、変数を選択するかを決定します。

### 指標

指標は数値であり、例は購入の回数です。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. **[!UICONTROL 「オーディエンス」]**&#x200B;タブの&#x200B;**「トリガー」[!UICONTROL セクションで以下の手順を実行します。]**

   1. **[!UICONTROL 「起動]** して **[!UICONTROL 存在]**&#x200B;する」などの標準イベントを選択します。
   1. カスタムのデータポイントであり、指標にマッピングされている 2 番目のトリガーを選択します。
   1. **[!UICONTROL 「番号]**」で、マッチャーオプションを選択します。

### 変数

変数はテキスト文字列からなる一意の識別子であり、例には国、空港などがあります。

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. **[!UICONTROL 「オーディエンス」]**&#x200B;タブの&#x200B;**「トリガー」[!UICONTROL セクションで以下の手順を実行します。]**

   1. **[!UICONTROL 「起動]** して **[!UICONTROL 存在]**&#x200B;する」などの標準イベントを選択します。
   1. カスタムのデータポイントであり、変数にマッピングされている 2 番目のトリガーを選択します。
   1. **[!UICONTROL 「テキスト]**」で、マッチャーオプションを選択します。

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
