---
description: ビデオ測定の一般的なプロセスは、AppMeasurement のすべてのプラットフォームでほぼ同一です。ここでは、開発者タスクの基本的な概要とコードサンプルを示します。
seo-description: ビデオ測定の一般的なプロセスは、AppMeasurement のすべてのプラットフォームでほぼ同一です。ここでは、開発者タスクの基本的な概要とコードサンプルを示します。
seo-title: ビデオ分析
title: ビデオ分析
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# ビデオ分析 {#video-analytics}

ビデオ測定の一般的なプロセスは、AppMeasurement のすべてのプラットフォームでほぼ同一です。ここでは、開発者タスクの基本的な概要とコードサンプルを示します。

For more information about Video measurement, see the Measuring audio and video in Adobe Analytics guide.  [](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)以下の表に、Analytics に送信されるメディアデータを示します。処理ルールを使用して、「コンテキストデータ変数」列のコンテキストデータを「変数の種類」列の Analytics 変数にマッピングします。

## プレイヤーイベントのAnalytics変数へのマッピング

* **a.media.name**

   （必須）訪問者が何らかの方法でビデオを視聴したときに、実装で指定されたビデオ名を収集します。この変数には分類を追加できます。

   **（オプション）** 「カスタムインサイト」変数は、ビデオパス情報を提供します。

   * Variable name: eVar
      * デフォルトの有効期限：訪問
      * カスタムインサイト（s.prop、ビデオパスに使用）

* **a.media.name**

   （**オプション**）ビデオパス情報を提供します。この変数に対して、ClientCare でパスを有効にする必要があります。

   * イベントタイプ：カスタムインサイト（s.prop）
   * カスタムインサイト（s.prop）

* **a.media.segment**

   （**必須**）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. デフォルトのビデオデータ収集方法では、ビデオの開始（再生）、セグメントの開始およびビデオの終了（停止）ポイントでデータが収集されます。

   Analytics は、訪問者が視聴を開始したときに最初のセグメントビューをセグメントの先頭としてカウントします。後続のセグメントビューは、セグメントの開始としてカウントされます。

   * Variable type: eVar
   * デフォルトの有効期限：ページビュー

* **a.contentType**

   訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。ビデオ測定によって送信されるヒットには、「ビデオ」のコンテンツタイプが割り当てられます。この変数は、ビデオ追跡専用に予約する必要はありません。同じ変数を使用する他のコンテンツレポートコンテンツタイプを使用することにより、異なるコンテンツのタイプでの訪問者の分布を分析できます。例えば、この変数を使用する「記事」や「製品ページ」などの値を使用して、他のコンテンツタイプにタグを付けることができます。ビデオ測定の見地からすると、コンテンツタイプを使用することによってビデオ訪問者を識別でき、その結果、ビデオのコンバージョン率を計算できます。

   * Variable type: eVar
   * デフォルトの有効期限：ページビュー

* **a.media.timePlayed**

   前回のデータ収集プロセス（イメージリクエスト）以降のビデオ視聴秒数をカウントします。

   * 変数型：イベント
   * タイプ：カウンター

* **a.media.view**

   訪問者がビデオの一部を視聴したことを示します。ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

   * 変数型：イベント
   * タイプ：カウンター

* **a.media.segmentView**

   訪問者がビデオセグメントの一部を視聴したことを示します。ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

   * 変数型：イベント
   * タイプ：カウンター

* **a .media.complete**

   ユーザーがビデオを最後まで視聴したことを示します。デフォルトでは、完了イベントはビデオが終了する 1 秒前に測定されます。導入時に、表示完了と見なすビデオの終わりからの秒数を指定できます。終わりが定義されないライブビデオやその他のストリーミングの場合は、完了を測定するためのカスタムポイントを指定できます。例えば、表示開始から特定の時間が経過したポイントなどです。

   * 変数型：イベント
   * タイプ：カウンター

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 例えば、プレーヤーが一時停止した場合は `mediaStop` が呼び出され、再生が開始または再開された場合は `mediaPlay` が呼び出されます。

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   追跡用のビデオを開きます。

   * このメソッドの構文を次に示します。

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   追跡用の `MediaSettings` オブジェクトを開きます。

   * このメソッドの構文を次に示します。

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Closes the media item named *`name`*.

   * このメソッドの構文を次に示します。

      ```cpp
      void close(QString name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * このメソッドの構文を次に示します。

      ```cpp
      void play(QString name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **complete**

   指定された&#x200B;*`offset`でメディアアイテムが再生完了された、と手動で記録します。*

   * このメソッドの構文を次に示します。

      ```cpp
      void complete(QString name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   指定された *offset* でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```cpp
      stop(QString name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```cpp
      void click(QString name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
