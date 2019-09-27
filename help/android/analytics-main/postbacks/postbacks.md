---
description: ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。
keywords: android;library;mobile;sdk
seo-description: ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。
seo-title: ポストバック
solution: Marketing Cloud,Analytics
title: ポストバックの概要
topic: 開発者と導入
uuid: 8bfd4374-2767-421d-891d-e1e9a9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# ポストバック {#postbacks}

ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。

>[!IMPORTANT]
>
>この機能には、SDKバージョン4.6.0以降が必要です。

ポストバックメッセージはキューに入れられ、分析データの収集を制御する既存のすべてのオンライン／オフラインルールに従います。（表示されたメッセージのように）メッセージが一致すると、ポストバックメッセージは残りのメッセージをキャンセルしません。これにより、同じ分析ヒットで複数のポストバックをおこなうことが可能になります。定義については、*postbacks* の行（[ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)を参照してください。

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. 現時点では、履歴またはセグメントに基づくデータは使用できません。

また、SDK が認識できる内部データに自動的に置き換えられる、特定の予約済みのテンプレートもあります。

これには以下が含まれます。

| トークン名 | トークンの説明 |
|--- |--- |
| {%sdkver%} | SDKのバージョンを返します。 |
| {%cachebust%} | 1 ～ 100000000 の間の乱数に解決されます。 |
| {%adid%} | Android 用の広告主 ID を返します。`submitAdvertisingIdentifierTask` を使用した場合にのみ機能します。 |
| {%pushid%} | プッシュ識別子トークンを返します。`setPushIdentifier` を使用した場合にのみ機能します。 |
| {%timestampu%} | 現在のタイムスタンプをエポックタイムで返します。 |
| {%timestampz%} | 現在のタイムスタンプを JavaScript（ISO 8601）形式で返します。 |