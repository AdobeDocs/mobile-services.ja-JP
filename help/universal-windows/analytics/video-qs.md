---
description: ビデオ分析に役立つ情報です。
seo-description: ビデオ分析に役立つ情報です。
seo-title: ビデオ分析
solution: Marketing Cloud,Analytics
title: ビデオ分析
topic: 開発者と導入
uuid: f45dac3b-cd2e-4fba-a3b2-c243640ecfa4
translation-type: tm+mt
source-git-commit: 1c0b7dadc28f772e903baa8605016e70f05081d7

---


# ビデオ分析 {#video-analytics}

ビデオ分析に役立つ情報です。

Video measurement is described in detail in the [Measuring video and audio in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guide. ビデオ測定の一般的なプロセスは、AppMeasurement のすべてのプラットフォームでほぼ同一です。このクイックスタートでは、開発者のタスクに関する基本的な概要とコード例を示します。

次の表に、Analytics に送信されるメディアデータのリストを示します。処理ルールを使用して、コンテキストデータをAnalytics変数にマップします。

* **a.media.name**

   (**Required**) Collects the name of the video, as specified in the implementation, when a visitor views the video in some way.You can add classifications for this variable.

   （**オプション**）カスタムインサイト変数は、ビデオパス情報を提供します。

   * 変数型：eVar
   * デフォルトの有効期限：訪問
   * カスタムインサイト（s.prop、ビデオパスに使用）

* **a.media.name**

   （**オプション**）ビデオパス情報を提供します。この変数に対して、ClientCare でパスを有効にする必要があります。

   * イベントタイプ：カスタムインサイト（s.prop）。
   * 変数型：カスタムインサイト(s.prop)

* **a.media.segment**

   （**必須**）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。

   この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segments eVar.

   デフォルトのビデオデータ収集方法では、ビデオの開始（再生）時、セグメントの開始時およびビデオの終了（停止）時にデータが収集されます。Analytics は、訪問者が視聴を開始したときに最初のセグメントビューをセグメントの先頭としてカウントします。後続のセグメントビューは、セグメントの開始としてカウントされます。

   * 変数型：eVar
   * デフォルトの有効期限：ページビュー

* **a.contentType**

   訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。ビデオ測定によって送信されるヒットには、「ビデオ」のコンテンツタイプが割り当てられます。この変数は、ビデオ追跡専用に予約する必要はありません。同じ変数を使用する他のコンテンツレポートコンテンツタイプを使用することにより、異なるコンテンツのタイプでの訪問者の分布を分析できます。例えば、この変数を使用する「記事」や「製品ページ」などの値を使用して、他のコンテンツタイプにタグを付けることができます。

   ビデオ測定の見地からすると、コンテンツタイプを使用することによってビデオ訪問者を識別でき、その結果、ビデオのコンバージョン率を計算できます。

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

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

ビデオの追跡に使用したい設定で `MediaSettings` オブジェクトを設定します。

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. 例えば、プレーヤーが一時停止した場合は `Stop` が呼び出され、再生が開始または再開された場合は `Play` が呼び出されます。

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

### Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS:settingsWith)**

   指定したパラメーターと共に `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS:adSettingsWith)**

   広告ビデオの追跡に使用する `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **開く(winJS:開く)**

   Tracks a media open using the settings defined in `settings`.

   * このメソッドの構文を次に示します。

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.open(mySettings);
      ```

* **閉じる(winJS:終了)**

   Tracks a media close for the media item named *`name`*.

   * このメソッドの構文を次に示します。

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **再生(winJS:再生)**

   指定された *offset`name`（秒）で指定された*** のメディアアイテムの再生を追跡します。

   * このメソッドの構文を次に示します。

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **完了(winJS:完了)**

   指定された&#x200B;*オフセット*&#x200B;でメディアアイテムが再生完了されたことを手動で記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **停止(winJS:停止)**

   指定された *offset* でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **(winJS:クリック)**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **追跡(winJS:トラック)**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      ADB.Media.track("mediaName",  null);
      ```
