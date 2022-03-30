---
description: ビデオ分析に役立つ情報です。
solution: Experience Cloud Services,Analytics
title: ビデオ分析
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 71%

---

# ビデオ分析 {#video-analytics}

ビデオ分析に役立つ情報です。

ビデオ指標について詳しくは、 [Adobe Analyticsでのストリーミングメディアの測定](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=ja) ガイド。 ビデオを測定する一般的なプロセスは、すべての AppMeasurement プラットフォームで非常に似ています。 このクイックスタートでは、開発者タスクの基本的な概要とコードサンプルを提供します。

次の表に、Analytics に送信されるメディアデータのリストを示します。処理ルールを使用して、コンテキストデータを Analytics 変数にマッピングします。

* **a.media.name**

   （必須）訪問者がビデオを何らかの方法で表示した場合に、実装で指定されているビデオの名前を収集します。この変数の分類を追加できます。

   （**オプション**）カスタムインサイト変数はビデオパス情報を提供します。

   * 変数型：eVar
   * デフォルトの有効期限：訪問
   * カスタムインサイト（s.prop、ビデオパスに使用）

* **a.media.name**

   （オプション）ビデオパス情報を提供します。この変数に対して、サポートでパスを有効にする必要があります。

   イベントタイプ：カスタムインサイト（s.prop）

   * 変数タイプ：カスタムインサイト（s.prop）

* **a.media.segment**

   （必須）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。例えば、訪問者がビデオの最初のセグメントを表示すると、SiteCatalystによって次の情報が `1:M:0-25` セグメントeVar。

   デフォルトのビデオデータ収集方法では、次の時点でデータが収集されます。

   * ビデオ開始（再生）
   * セグメント開始
   * ビデオ終了（停止）

   Analytics は、訪問者開始が視聴しているときに、最初のセグメント表示をセグメントの開始でカウントします。後続のセグメントは、セグメントの開始時に表示されます。

   * 変数型：eVar
   * デフォルトの有効期限：ページビュー


* **a.contentType**

   訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。ビデオ指標によって送信されるヒットには、「ビデオ」というコンテンツタイプが割り当てられます。 この変数は、ビデオトラッキング専用に予約する必要はありません。 同じ変数を使用する他のコンテンツレポートコンテンツタイプを使用することで、異なるコンテンツのタイプでの訪問者の分布を分析できます。 例えば、この変数を使用する「記事」や「製品ページ」などの値を使用して、他のコンテンツタイプにタグを付けることができます。 ビデオ指標の見地からすると、コンテンツタイプを使用することで、ビデオ訪問者を識別して、ビデオのコンバージョン率を計算できます。

   * 変数型：eVar
   * デフォルトの有効期限：ページビュー

* **a.media.timePlayed**

   前回のデータ収集プロセス（イメージリクエスト）以降のビデオ視聴秒数をカウントします。

   * 変数型：イベント
   * タイプ：カウンター

* **a.media.view**

   訪問者がビデオの一部を視聴したことを示します。ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

   * 変数：イベント
   * タイプ：カウンター

* **a.media.segmentView**

   訪問者がビデオセグメントの一部を視聴したことを示します。ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

   * 変数型：イベント
   * タイプ：カウンター

* **a .media.complete**

   ユーザーがビデオを最後まで視聴したことを示します。デフォルトでは、完了イベントはビデオが終了する 1 秒前に測定されます。導入時に、表示完了と見なすビデオの終わりからの秒数を指定できます。終わりが定義されないライブビデオやその他のストリーミングの場合は、完了を測定するためのカスタムポイントを指定できます。例えば、表示開始から特定の時間が経過したポイントなどです。

   * 変数型：イベント
   * タイプ：カウンター

## メディア設定の指定 {#section_929945D4183C428AAF3B983EFD3E2500}

ビデオの追跡に使用したい設定で `MediaSettings` オブジェクトを設定します。

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## プレーヤーイベントの追跡 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

ビデオの再生を測定するには、`Play`、`Stop` および `Close` メソッドを適切なときに呼び出す必要があります。例えば、プレーヤーが一時停止した場合は `Stop` が呼び出され、再生が開始または再開された場合は `Play` が呼び出されます。

## クラス {#section_16838332727348F990305C0C6B0D795C}

### クラス：MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## メディア測定クラスとメソッドのリファレンス {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS:settingsWith)**

   指定したパラメーターと共に `MediaSetting` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS:adSettingsWith**

   広告ビデオの追跡に使用する `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **開く (winJS:開く )**

   で定義された設定を使用して、メディアの開封をトラッキングします。 `settings`.

   * このメソッドの構文を次に示します。

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.open(mySettings); 
      ```

* **閉じる (winJS:閉じる )**

   次の名前のメディアアイテムのメディア終了をトラッキングします： *名前*.

   * このメソッドの構文を次に示します。

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.close("mediaName");
      ```

* **再生 (winJS:再生 )**

   次の名前のメディアアイテムのメディア再生をトラッキングします： *`name`* 与えられた *オフセット* （秒単位）。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **完了 (winJS:完了 )**

   指定された&#x200B;*オフセット*&#x200B;でメディアアイテムが再生完了されたことを手動で記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **停止 (winJS:停止 )**

   指定された *offset* でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **クリック (winJS:クリック )**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **追跡 (winJS:トラック )**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.track("mediaName", null);
      ```
