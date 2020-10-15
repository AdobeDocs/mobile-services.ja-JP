---
description: アプリでモバイル Web コンテンツを開く場合は、ネイティブとモバイル Web の間を移動する訪問者が別々に識別されないようにします。
seo-description: アプリでモバイル Web コンテンツを開く場合は、ネイティブとモバイル Web の間を移動する訪問者が別々に識別されないようにします。
seo-title: アプリとモバイル Web にまたがる訪問者トラッキング
solution: Experience Cloud,Analytics
title: アプリとモバイル Web にまたがる訪問者トラッキング
topic: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '508'
ht-degree: 100%

---


# アプリとモバイル Web にまたがる訪問者トラッキング {#visitor-tracking-between-an-app-and-mobile-web}

アプリでモバイル Web コンテンツを開く場合は、ネイティブとモバイル Web の間を移動する訪問者が別々に識別されないようにします。

## アプリの訪問者 ID

アプリがインストールされると、Android SDK は、一意の訪問者 ID を生成します。この ID はモバイルデバイスの永続的なメモリに保存され、ヒットのたびに送信され、ユーザーがアプリをアンインストールした場合にのみ削除されます。

>[!TIP]
>
>アプリの訪問者 ID は、アップグレード後も保持されます。

## モバイル Web の訪問者 ID

一般的なモバイル Web 実装では、デスクトップサイトで使用されているのと同じ標準の Analytics `s_code.js` または `AppMeasurement.js` を使用します。JavaScript ライブラリには、一意の訪問者 ID を生成する独自メソッドがあり、アプリからモバイル Web コンテンツを開くと、異なる訪問者 ID が生成される原因となります。

## アプリとモバイル Web にまたがる訪問者トラッキング {#section_1755BCCFD42D456EB2319141030FDDFF}

アプリとモバイル Web で同じ訪問者 ID を使用するには、以下のようにします。

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. Web ビューを開くために使用される URL に訪問者情報を追加するために、`visitorAppendToURL` を呼び出します。

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   あるいは、SDK バージョン 4.16.0 以降では、`Visitor.getUrlVariablesAsync` を呼び出して独自の URL を生成できます。

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

アドビに新しい ID のリクエストを送信するのではなく、宛先ドメインの ID サービスコードによって、URL から MID が抽出されます。コードは、MID で渡された値を使用して訪問者を追跡します。

モバイル Web コンテンツからヒットがあったら、各ヒットに `mid` パラメーターが存在すること、およびこの値がアプリコードによって送信された `mid` パラメーターと一致することを確認します。

## 訪問者トラッキングのトラブルシューティング {#section_9B641F8569E34A089C52AA28EA4C891D}

### `Visitor.appendToURL` が見つかりません。

親アプリケーションにバンドルされている Adobe SDK がバージョン 4.12.0 以上であることを確認します。

**URL に Adobe ID が表示されません。**

* 以下を確認します。
   * Web ビューを開くための URL 文字列が `Visitor.appendToURL(urlString)` によって生成されている。
   * Adobe ID がエンコードされている。開かれている URL に追加されている ID を確認するには、その URL に `adobe_mc` クエリーパラメーターが表示されていることを確認します。

### アプリと Web ビューで `mid` が同一ではありません。

* 以下を確認します。

   * Web ビューを開くための URL 文字列が `Visitor.appendToURL(urlString)` によって生成されている。
   * URL 文字列に Adobe パラメーターが含まれている。

      文字列には `adobe_mc="SAMPLE_ID_DATA"` が含まれている必要があります。ここで、`"SAMPLE_ID_DATA"` は Adobe Mobile SDK で生成された ID になります。
   * `VisitorAPI.js` がバージョン 1.7.0 以上である。

これらのトラブルシューティング手順で問題が解決しない場合は、Adobe Experience Care にお問い合わせください。

>[!IMPORTANT]
>
>アドビが実装を検証できるようにするには、サンプルアプリケーションおよび関連するサイトを共有する必要があります。

