---
description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-description: 処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。
seo-title: 処理ルールとコンテキストデータ
solution: Experience Cloud,Analytics
title: 処理ルールとコンテキストデータ
topic: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 48%

---


# 処理ルールとコンテキストデータ{#processing-rules-and-context-data}

処理ルールは、コンテキストデータ変数で送信したデータを、レポート用に eVar や prop などの変数にコピーするために使用します。詳しくは、「[処理ルール](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

処理ルールを使用する際には、次の情報に留意してください。

* 論理的な順序を維持するのに役立つので、名前空間を使用してコンテキストデータ変数をグループ化します。 例えば、製品に関する情報を収集するには、次の変数を定義します。

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 処理ルールインターフェイスでは、コンテキストデータ変数がアルファベット順に並べ替えられるので、同じ名前空間にある変数をすばやく確認できます。

   evarまたはprop番号を使用して、コンテキストデータキーに名前を付けないでください。

   ```js
   "eVar1":"jimbo"
   ```

   This might make it *slightly* easier when you complete the one-time mapping in processing rules, but you lose readability during debugging and future code updates, which can be more difficult. 代わりに、キーと値には説明的な名前を使用することを強くお勧めします。

   ```js
   "username":"jimbo"
   ```

* カウンターイベントを定義するコンテキスト変数は1に設定する必要があります。

   ```js
   "logon":"1"
   ```

* 増分イベントを定義するコンテキストデータ変数は、イベントをキーとして持つことができ、増分量を値として持つことができます。

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>アドビは名前空間「`"a."`」を予約します。他に競合を回避するうえでの要件は、コンテキストデータ変数がログイン会社内で一意であることだけです。

