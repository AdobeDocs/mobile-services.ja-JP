---
description: ビデオを測定する一般的なプロセスは、すべての AppMeasurement プラットフォームで非常に似ています。 ここでは、開発者タスクの基本的な概要とコードサンプルを示します。
title: ビデオ分析
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
exl-id: 90da1a9e-2faa-429c-969e-869ebedf08cc
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 67%

---

# ビデオ分析 {#video-analytics}

ビデオを測定する一般的なプロセスは、すべての AppMeasurement プラットフォームで非常に似ています。 ここでは、開発者タスクの基本的な概要とコードサンプルを示します。

ビデオ測定について詳しくは、『Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ja) でのストリーミングメディアの測定』ガイドを参照してください。  [次の表に、Analytics に送信されるメディアデータのリストを示します。処理ルールを使用して、「コンテキストデータ変数」列のコンテキストデータを、「変数の種類」列の説明に従って Analytics 変数にマッピングします。

## プレーヤーイベントの Analytics 変数へのマッピング

* **a.media.name**

   （必須）訪問者が何らかの方法でビデオを表示した場合に、実装で指定されているビデオの名前を収集します。この変数の分類を追加できます。

   **（オプション）** Custom Insight変数はビデオパス情報を提供します。

   * 変数名：eVar
      * デフォルトの有効期限：訪問
      * カスタムインサイト（s.prop、ビデオパスに使用）

* **a.media.name**

   （**オプション**）ビデオパス情報を提供します。この変数に対して、サポートでパスを有効にする必要があります。

   * イベントタイプ：カスタムインサイト（s.prop）
   * Custom Insight(s.prop)

* **a.media.segment**

   （**必須**）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。

   例えば、訪問者がビデオの最初のセグメントを表示すると、SiteCatalystは SegmentseVarに `1:M:0-25` を収集する場合があります。 デフォルトのビデオデータ収集方法では、ビデオの開始（再生）、セグメントの開始、ビデオの終了（停止）時点でデータが収集されます。

   Analytics は、訪問者開始が視聴しているときに、最初のセグメント表示をセグメントの開始でカウントします。後続のセグメントは、セグメントの開始時に表示されます。

   * 変数型：eVar
   * デフォルトの有効期限：ページビュー

* **a.contentType**

   訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。ビデオ指標によって送信されるヒットには、「ビデオ」のコンテンツタイプが割り当てられます。 この変数は、ビデオトラッキング専用に予約する必要はありません。 同じ変数を使用する他のコンテンツレポートコンテンツタイプを使用することで、異なるコンテンツのタイプでの訪問者の分布を分析できます。 例えば、この変数を使用する「記事」や「製品ページ」などの値を使用して、他のコンテンツタイプにタグを付けることができます。 ビデオ測定の見地からすると、コンテンツタイプを使用することによってビデオ訪問者を識別でき、その結果、ビデオのコンバージョン率を計算できます。

   * 変数型：eVar
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

## プレーヤーイベントの追跡 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

ビデオの再生を測定するには、`mediaPlay`、`mediaStop` および `mediaClose` メソッドを適切なときに呼び出す必要があります。例えば、プレーヤーが一時停止した場合は `mediaStop` が呼び出され、再生が開始または再開された場合は `mediaPlay` が呼び出されます。

## メディア測定クラスとメソッドのリファレンス {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   追跡するビデオを開きます。

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

   *`name`* という名前のメディアアイテムを閉じます。

   * このメソッドの構文を次に示します。

      ```cpp
      void close(QString name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   *`name`* という名前のメディアアイテムを指定の *`offset`*（秒単位）で再生します。

   * このメソッドの構文を次に示します。

      ```cpp
      void play(QString name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **complete**

   指定された *`offset`* の時点でメディアアイテムが完了したことを手動で記録します。

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
