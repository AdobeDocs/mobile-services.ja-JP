---
description: ポストバックを使用すると、SDKによって収集されたデータをサードパーティのサーバーに送信できます。 アプリ内メッセージの表示に使用するのと同じトリガーと特徴を活用することで、カスタマイズしたデータをサードパーティのサーバーに送信するようにSDKを設定できます。
seo-description: ポストバックを使用すると、SDKによって収集されたデータをサードパーティのサーバーに送信できます。 アプリ内メッセージの表示に使用するのと同じトリガーと特徴を活用することで、カスタマイズしたデータをサードパーティのサーバーに送信するようにSDKを設定できます。
seo-title: ポストバック
solution: Experience Cloud,Analytics
title: ポストバックの概要
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 28%

---


# ポストバックの概要 {#postbacks}

ポストバックを使用すると、SDKによって収集されたデータをサードパーティのサーバーに送信できます。 アプリ内メッセージの表示に使用するのと同じトリガーと特徴を活用することで、カスタマイズしたデータをサードパーティのサーバーに送信するようにSDKを設定できます。

>[!IMPORTANT]
>
>この機能には、SDK バージョン 4.6.0 以降が必要です。

ポストバックメッセージはキューに登録され、分析データ収集を制御する既存のオンライン/オフラインのルールに従います。 メッセージが一致した場合（表示されたメッセージと同様）、ポストバックメッセージは残りのメッセージをキャンセルしません。 これにより、同じ解析ヒットで複数のポストバックを行うことができます。 定義については、*postbacks* の行[ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)を参照してください。

## テンプレートの拡張 {#section_6758AD05A24C4E9E965F5253294C164A}

テンプレート拡張は、`templateurl` プロパティと `templatebody` プロパティの両方で使用できます。テンプレート項目には `{key}` という形式を使用します。ここで、`key` は、コンテキストデータキーまたは従来のデータキーです。The values available for template expansion are limited to the [standard Lifecycle variables list](/help/ios/metrics.md), in addition to any custom data attached to the hit that triggers the message. 現時点では、履歴ベースまたはセグメントベースのデータは使用できません。

また、SDKが自動的にSDKが認識する内部データで置き換える、予約済みの固有のテンプレートもあります。

例えば、次のものがあります。

| トークン名 | トークンの説明 |
|--- |--- |
| `{%sdkver%}` | SDK のバージョンを返します。 |
| `{%cachebust%}` | 1 ～ 100000000 の間の乱数に解決されます。 |
| `{%adid%}` | IDFA を返します。このトークンは、`setAdvertisingIdentifier` を使用した場合にのみ機能します。 |
| `{%pushid%}` | プッシュ識別子トークンを返します。このトークンは、`setPushIdentifier` を使用した場合にのみ機能します。 |
| `{%timestampu%}` | 現在のタイムスタンプをエポックタイムで返します。 |
| `{%timestampz%}` | 現在のタイムスタンプを JavaScript（ISO 8601）形式で返します。 |