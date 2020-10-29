---
description: この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。
seo-title: Adobe Mobile Services でのディープリンクの追跡
solution: Experience Cloud,Analytics
title: ディープリンクの追跡
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: ht
source-git-commit: e28340249c22d9f121d5c21205227ee758fb9e1b
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# ディープリンクの追跡

この情報は、Adobe Mobile Android SDK を使用して、モバイルアプリのディープリンクおよびディファードディープリンクを追跡する場合に役立ちます。

## ディープリンクの追跡

1. SDK をプロジェクトに追加し、ライフサイクル指標を実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. URL を処理するアプリケーションを登録します。

   詳しくは、「[URL](https://developer.android.com/training/basics/intents/filters.html)」を参照してください。
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

Adobe Mobile SDK は、任意のディープリンクまたはユニバーサルリンクに `a.deeplink.id` というラベルを持つキーと、対応する null 以外のユーザー生成値が含まれる場合、そのリンクに追加されたデータのキーと値のペアを解析できます。リンクに `a.deeplink.id` キーと値が含まれる場合、そのリンクに追加されたデータのすべてのキーと値のペアが解析され、ライフサイクルヒットに添付されて、Adobe Analytics に送信されます。

さらに、以下の 1 つ以上の予約済みキー（とユーザー生成値）をディープリンクまたはユニバーサルリンクに追加することもできます。

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

これらのキーは、Adobe Analytics でのレポート用にあらかじめマッピングされている変数です。マッピングと処理ルールについて詳しくは、「[処理ルールとコンテキストデータ](https://docs.adobe.com/content/help/ja-JP/analytics/admin/admin-tools/processing-rules/processing-rules.html)」を参照してください。

## ディファードディープリンクのトラッキング（マーケティングリンクで使用）

ディファードディープリンクを使用する場合、Adobe SDK は、インテントデータとしてディープリンクを持つ新しいインテントを開きます。このプロセスは、上記のコードを使用して、外部ディープリンクとして処理されます。

## ディープリンク公開情報 {#section_1815396353614DA8A63D8D92112217E7}

### 定数

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

