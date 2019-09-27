---
description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-title: 処理ルールとコンテキストデータ
solution: Marketing Cloud,Analytics
title: 処理ルールとコンテキストデータ
topic: 開発者と導入
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

処理ルールを使用する際には、次の情報に留意してください。

* コンテキストデータ変数は、名前空間を使用してグループ化します。これは、論理的な順序を維持するのに役立ちます。例えば、ある製品の情報を収集するために、次の変数を定義できます。

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* コンテキストデータ変数は、処理ルールインターフェイスでアルファベット順に並べ替えられます。そのため、同じ名前空間に属している変数がすぐにわかります。

   コンテキストデータキーの名前には、eVar 番号および prop 番号を使用しないようにします。

   ```js
   "eVar1":"jimbo"
   ```

   これらの番号を使用すると、処理ルールで 1 回のみのマッピングを作成する際に作業が&#x200B;*多少*&#x200B;容易になる可能性はあります。しかし、デバッグ中や後でコードを更新するときにわかりにくくなり、作業が困難になるおそれがあります。そのため、キーと値にはわかりやすい名前を付けることを強くお勧めします。

   ```js
   "username":"jimbo"
   ```

* カウンターイベントを定義するコンテキスト変数は、1 に設定します。

   ```js
   "logon":"1"
   ```

* 増分イベントを定義するコンテキストデータ変数では、イベントをキーに、増分する量を値に設定することができます。

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>アドビは名前空間を予約しま `"a."`す。 他に競合を回避するうえでの要件は、コンテキストデータ変数がログイン会社内で一意であることだけです。

