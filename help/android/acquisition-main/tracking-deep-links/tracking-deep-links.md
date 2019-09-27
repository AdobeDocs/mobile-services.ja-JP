---
description: この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。
seo-title: Adobe Mobile Servicesでのディープリンクの追跡
solution: Marketing Cloud,Analytics
title: ディープリンクの追跡
topic: 開発者と導入
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。

## ディープリンクの追跡

1. SDK をプロジェクトに追加し、ライフサイクル指標を実装します。

   詳しくは、「SDKと設定フ *ァイルをIntelliJ IDEAに追加する」または「コア実装とライフサイクルのEclipse* Project [」を参照してください](/help/android/getting-started/dev-qs.md)。

1. URL を処理するアプリケーションを登録します。

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
1. `collectLifecycleData` を使用して、ディープリンクインテントが含まれたアクティビティを Adobe SDK に渡します。

   以下に、ディープリンクの追跡例を示します。

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

さらに、次の予約済みキー（ユーザ生成値付き）のうち1つ以上をディープリンクまたはユニバーサルリンクに追加できます。

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

これらのキーは、Adobe Analytics でのレポート用にあらかじめマッピングされている変数です。マッピングと処理ルールについて詳しくは、[処理ルールとコンテキストデータ](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)を参照してください。

## Tracking deferred deep links (for use with Marketing Links)

ディファードディープリンクにより、ディープリンクがインテントデータとして含まれた新しいインテントが Adobe SDK によって開かれます。このプロセスは、前述のコードを使用して外部ディープリンクとして処理されます。

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### 定数

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

