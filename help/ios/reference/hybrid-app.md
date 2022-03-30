---
description: アプリでモバイル Web コンテンツを開く場合は、訪問者がネイティブアプリからモバイル Web に移動したり、その逆に移動したりしても、別の訪問者として識別されないようにする必要があります。
solution: Experience Cloud Services,Analytics
title: アプリとモバイル Web にまたがる訪問者トラッキング
topic-fix: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
exl-id: d8459d59-0edd-42c4-81b5-529b250accb4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 100%

---

# アプリとモバイル Web にまたがる訪問者トラッキング   {#visitor-tracking-between-an-app-and-mobile-web}

アプリでモバイル Web コンテンツを開く場合は、訪問者がネイティブアプリからモバイル Web に移動したり、その逆に移動したりしても、別の訪問者として識別されないようにする必要があります。

## アプリの訪問者 ID

アプリがインストールされると、iOS SDK は一意の訪問者 ID を生成します。この ID はモバイルデバイスの永続的なメモリに保存され、ヒットのたびに送信されます。この ID が削除されるのは、ユーザーがアプリをアンインストールしたときだけです.

>[!TIP]
>
>アプリの訪問者 ID は、アップグレード後も保持されます。

## モバイル Web の訪問者 ID

一般的なモバイル Web 実装では、デスクトップサイトで使用されているのと同じ標準の Analytics `s_code.js` または `AppMeasurement.js` を使用します。JavaScript ライブラリには、一意の訪問者 ID を生成する独自メソッドがあり、アプリからモバイル Web コンテンツを開くと、異なる訪問者 ID が生成される原因となります。

アプリとモバイル Web で同じ訪問者 ID を使用するには、URL でアプリの訪問者 ID をモバイル Web に渡します。

## アプリとモバイル Web にまたがる訪問者トラッキングの実装 {#section_EDC91D6C67AD43999227707C2769C65D}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/ios/getting-started/dev-qs.md)の「*プロジェクトへの SDK と設定ファイルの追加*」を参照してください。
1. Web ビューを開くために使用される URL に訪問者情報を追加するために、`visitorAppendToURL` を呼び出します。

   ```objective-c
   NSURL *url = [NSURL URLWithString:@"https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   あるいは、SDK バージョン 4.16.0 以降では、`visitorGetUrlVariablesAsync:` を呼び出して独自の URL を生成できます。

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

アドビに新しい ID のリクエストを送信するのではなく、宛先ドメインの ID サービスコードによって、URL から MID が抽出されます。宛先ページの ID サービスコードは、MID で渡された値を使用して訪問者を追跡します。

モバイル Web コンテンツからのヒットが発生したら、各ヒットに `mid` パラメーターが存在することと、この値がアプリのコードによって送信される `mid` と一致していることを確認します。

## 訪問者トラッキングのトラブルシューティング {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### `[ADBMobile visitorAppendToURL:]` が見つかりません。

親アプリケーションにバンドルされている Adobe SDK がバージョン 4.12.0 以上であることを確認します。

### URL に Adobe ID が表示されません。

以下を確認します。

* Web ビューを開くための URL 文字列が `[ADBMobile visitorAppendToURL:]` によって生成されている。

* Adobe ID がエンコードされている。

   開く URL に ID が追加されていることを確認するには、`adobe_mc` クエリパラメーターを調べてください。

### アプリと Web ビューの「mid」が同一ではありません。*

以下を確認します。

* Web ビューを開くための URL 文字列が `[ADBMobile visitorAppendToURL:]` によって生成されている。

   URL 文字列に Adobe パラメーターが含まれている。

   文字列には `adobe_mc="SAMPLE_ID_DATA"` が含まれている必要があります。ここで、`"SAMPLE_ID_DATA"` は Adobe Mobile SDK で生成された ID になります。

* `VisitorAPI.js` がバージョン 1.7.0 以上である。

これらのトラブルシューティング手順で問題が解決しない場合は、Adobe Client Care にご連絡ください。アドビが実装を検証できるよう、サンプルアプリケーションや関連サイトを共有する準備をしてください。
