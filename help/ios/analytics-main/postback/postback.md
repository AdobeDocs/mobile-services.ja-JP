---
description: ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。
seo-description: ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。
seo-title: ポストバック
solution: Marketing Cloud、Analytics
title: ポストバックの概要
uuid: 25e2a5fb-1203-40dd-96cd- b23e0f23376d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# ポストバックの概要 {#postbacks}

ポストバックを使用すると、SDK によって収集されたデータをサードパーティのサーバーに送信できます。アプリ内メッセージを表示するために使用しているのと同じトリガーおよび特性を活用して、カスタマイズしたデータをサードパーティのサーバーに送信するように SDK を設定できます。

>[!IMPORTANT]
>
>この機能には、SDKバージョン4.6.0以降が必要です。

ポストバックメッセージはキューに入れられ、分析データの収集を制御する既存のすべてのオンライン／オフラインルールに従います。（表示されたメッセージのように）メッセージが一致すると、ポストバックメッセージは残りのメッセージをキャンセルしません。これにより、同じ分析ヒットで複数のポストバックをおこなうことが可能になります。定義については、*postbacks* の行（[ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)を参照してください。

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. テンプレート拡張に使用できる値は、[標準ライフサイクル変数リスト](/help/ios/metrics.md)およびメッセージをトリガーするヒットに添付されたカスタムデータに限定されます。現時点では、履歴またはセグメントに基づくデータは使用できません。

SDK が既知の内部データで自動的に置き換えをおこなう固有の予約済みテンプレートもあります。

例えば、次のものがあります。

| トークン名 | トークンの説明 |
|--- |--- |
| `{%sdkver%}` | SDK のバージョンを返します。 |
| `{%cachebust%}` | 1 ～ 100000000 の間の乱数に解決されます。 |
| `{%adid%}` | IDFA を返します。このトークンは、使用 `setAdvertisingIdentifier`した場合にのみ機能します。 |
| `{%pushid%}` | プッシュ識別子トークンを返します。このトークンは、使用 `setPushIdentifier`した場合にのみ機能します。 |
| `{%timestampu%}` | 現在のタイムスタンプをエポックタイムで返します。 |
| `{%timestampz%}` | 現在のタイムスタンプを JavaScript（ISO 8601）形式で返します。 |