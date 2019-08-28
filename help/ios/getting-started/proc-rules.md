---
description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-title: 処理ルールとコンテキストデータ
solution: Marketing Cloud、Analytics
title: 処理ルールとコンテキストデータ
topic: 開発者と導入
uuid: 51338pcm- fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。

詳しくは、以下のコンテンツを参照してください。

* [処理ルールのトレーニング](https://tv.adobe.com/embed/1181/16506/)（Summit 2013）
* 処理ルールを使用する権限があります

   処理ルールについて詳しくは [、処理ルールの概要](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)を参照してください。

処理ルールを使用する際には、次の情報に留意してください。

* コンテキストデータ変数は、名前空間を使用してグループ化します。これは、論理的な順序を維持するのに役立ちます。

   例えば、ある製品に関する情報を収集する場合、以下の変数を定義できます。

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

   この命名方法を使用すると、処理ルールで 1 回限りのマッピングを実行するときの手間は若干減りますが、コードが読みにくくなるので、デバッグや将来のコード更新が困難になる可能性があります。**&#x200B;代わりに、キーと値にはわかりやすい名前を使用します。

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
>アドビが名前空間「 `a.`」を予約しています。この制約の他に、衝突を回避するために従うべき唯一の要件は、コンテキストデータ変数をログイン会社内で一意にすることです。

