---
description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar、prop およびその他の変数にコピーするために使用されます。
solution: Experience Cloud Services,Analytics
title: 処理ルールとコンテキストデータ
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 72%

---

# 処理ルールとコンテキストデータ  {#processing-rules-and-context-data}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar、prop およびその他の変数にコピーするために使用されます。 詳しくは、「[処理ルール](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

処理ルールを使用する際には、次の情報に留意してください。

* 論理的な順序を維持できるよう、名前空間を使用してコンテキストデータ変数をグループ化します。例えば、製品に関する情報を収集する場合、次の変数を定義できます。

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 処理ルールインターフェイスでは、コンテキストデータ変数がアルファベット順に並べ替えられるので、同じ名前空間内の変数をすばやく確認できます。

   データまたは prop 番号を使用して、コンテキストeVarキーに名前を付けないでください。

   ```js
   "eVar1":"jimbo"
   ```

   この命名方法を使用すると、処理ルールで 1 回限りのマッピングを完了するときの手間は&#x200B;*若干*&#x200B;減りますが、コードが読みにくくなるので、デバッグや将来のコード更新が困難になる可能性があります。代わりに、キーと値には説明的な名前を使用することを強くお勧めします。

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
>アドビは名前空間「`"a."`」を予約します。他に競合を回避するうえでの要件は、コンテキストデータ変数がログイン会社内で一意であることだけです。
