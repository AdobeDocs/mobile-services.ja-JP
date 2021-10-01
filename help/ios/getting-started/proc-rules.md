---
description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar、prop およびその他の変数にコピーするために使用します。
solution: Experience Cloud,Analytics
title: 処理ルールとコンテキストデータ
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 70%

---

# 処理ルールとコンテキストデータ {#processing-rules-and-context-data}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar、prop およびその他の変数にコピーするために使用します。

詳しくは、以下のコンテンツを参照してください。

* [処理ルールトレーニング](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013
* 処理ルールを使用するための承認の取得

   処理ルールについて詳しくは、Adobe Analyticsのドキュメントの [ 処理ルールの概要 ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) を参照してください。

処理ルールを使用する際には、次の情報に留意してください。

* 論理的な順序を維持できるよう、名前空間を使用してコンテキストデータ変数をグループ化します。

   例えば、製品に関する情報を収集する場合、次の変数を定義できます。

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 処理ルールインターフェイスでは、コンテキストデータ変数がアルファベット順に並べ替えられるので、同じ名前空間内の変数をすばやく確認できます。

   コンテキストデータキーには、eVarまたは prop 番号を使用して命名しないでください。

   ```js
   "eVar1":"jimbo"
   ```

   この命名方法を使用すると、処理ルールで 1 回限りのマッピングを実行するときの手間は&#x200B;*若干*&#x200B;減りますが、コードが読みにくくなるので、デバッグや将来のコード更新が困難になる可能性があります。代わりに、キーと値にはわかりやすい名前を使用してください。

   ```js
   "username":"jimbo"
   ```

* カウンターイベントを定義するコンテキスト変数は「1」に設定する必要があります。

   ```js
   "logon":"1"
   ```

* 増分イベントを定義するコンテキストデータ変数は、キーをイベント、値を増分量にすることができます。

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>アドビは名前空間「`a.`」を予約します。この制約の他に、衝突を回避するために従うべき唯一の要件は、コンテキストデータ変数をログイン会社内で一意にすることです。
