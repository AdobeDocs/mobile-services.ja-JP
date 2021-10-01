---
description: ポストバックを使用すれば、SDK で収集されたデータを、サードパーティのサーバーに送信できます。アプリ内メッセージの表示に使用するのと同じトリガーと特性を活用して、カスタマイズしたデータをサードパーティの宛先に送信するように SDK を設定できます。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud,Analytics
title: ポストバックの概要
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 100%

---

# ポストバック {#postbacks}

ポストバックを使用すれば、SDK で収集されたデータを、サードパーティのサーバーに送信できます。アプリ内メッセージの表示に使用するのと同じトリガーと特性を活用して、カスタマイズしたデータをサードパーティの宛先に送信するように SDK を設定できます。

>[!IMPORTANT]
>
>この機能には、SDK バージョン 4.6.0 以降が必要です。

ポストバックメッセージはキューに登録され、分析データ収集を制御する、オンラインとオフラインの既存のルールすべてに従います。メッセージが一致した場合（表示されたメッセージと同様）、ポストバックメッセージは残りのメッセージをキャンセルしません。これにより、同じ分析ヒットで複数のポストバックを実行できます。定義については、*postbacks* の行（[ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)）を参照してください。

## テンプレートの拡張 {#section_6758AD05A24C4E9E965F5253294C164A}

テンプレートの拡張は、`templateurl` プロパティと `templatebody` プロパティで使用できます。テンプレート項目には `{key}` という形式を使用します。ここで、`key` は、コンテキストデータキーまたは従来のデータキーです。テンプレートの拡張に使用できる値は、メッセージをトリガーするヒットにアタッチされるカスタムデータに加えて、[ライフサイクル指標](/help/android/metrics.md)に限られます。現時点では、履歴ベースのデータやセグメントベースのデータは使用できません。

また、SDK が、自動的に既知の内部データと置き換える、具体的な予約済みのテンプレートも用意されています。

例えば、次のものがあります。

| トークン名 | トークンの説明 |
|--- |--- |
| {%sdkver%} | SDK のバージョンを返します。 |
| {%cachebust%} | 1 ～ 100000000 の間の乱数に解決されます。 |
| {%adid%} | Android 用の広告主 ID を返します。`submitAdvertisingIdentifierTask` を使用した場合にのみ機能します。 |
| {%pushid%} | プッシュ識別子トークンを返します。`setPushIdentifier` を使用した場合にのみ機能します。 |
| {%timestampu%} | 現在のタイムスタンプをエポックタイムで返します。 |
| {%timestampz%} | 現在のタイムスタンプを JavaScript（ISO 8601）形式で返します。 |
