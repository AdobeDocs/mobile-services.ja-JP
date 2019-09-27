---
description: ビデオ測定ソリューションを使用して Android でビデオを測定する方法について説明します。
keywords: android;library;mobile;sdk
seo-description: ビデオ測定ソリューションを使用して Android でビデオを測定する方法について説明します。
seo-title: ビデオ分析
solution: Marketing Cloud,Analytics
title: ビデオ分析
topic: 開発者と導入
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# ビデオ分析 {#video-analytics}

ビデオ測定ソリューションを使用して Android でビデオを測定する方法について説明します。

>[!TIP]
>
>ビデオの再生中に、頻繁な「ハートビート」コールが送信され、再生時間を測定します。これらのハートビート呼び出しは、10 秒ごとに送信されるので、ビデオエンゲージメント指標やビデオフォールアウトレポートがより正確になります。アドビのビデオ測定ソリューションについて詳しくは、「Adobe Analyticsでのオ [ーディオとビデオの測定」を参照してください](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)。

ビデオを測定する一般的なプロセスは、どのプラットフォームでも同様です。ここでは、開発者タスクの概要とコードサンプルを提示します。次の表に、Analytics に送信されるメディアデータのリストを示します。処理ルールは、コンテキストデータをAnalytics変数にマップするために使用されます。

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * 変数型：eVar
      * デフォルトの有効期限：訪問
      * カスタムインサイト（s.prop、ビデオパスに使用）
   * （**必須**）訪問者が何らかの方法でビデオを表示すると、このコンテキストデータ変数は、実装に指定されているビデオの名前を収集します。この変数では分類を追加できます。
   * （**オプション**）カスタムインサイト変数は、ビデオパス情報を提供します。

* **a.media.name**
   * 変数型：カスタムインサイト(s.prop)
   * （**オプション**）ビデオパス情報を提供します。

      >[!IMPORTANT]
      >
      >この変数に対してExpCareによってパスが有効にされている必要があります。
   * イベントタイプ：カスタムインサイト（s.prop）

* **a.media.segment**
   * Variable type: eVar
   * デフォルトの有効期限：ページビュー
   * （**必須**）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。

      この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the Segments eVar: `1:M:0-25`.

      デフォルトのビデオデータ収集メソッドでは、次の時点のデータが収集されます。

      * ビデオの開始（再生）
      * セグメントの開始
      * ビデオの終了（停止）
      Analytics は、訪問者が視聴を開始したときに最初のセグメントビューをセグメントの先頭としてカウントします。後続のセグメントビューは、セグメントの開始としてカウントされます。


* **a.contentType**
   * Variable type: eVar
   * デフォルトの有効期限：ページビュー
   * 訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。

      ビデオ指標によって送信されるヒットには、`video` というコンテンツタイプが割り当てられます。ビデオ指標の見地からすると、**コンテンツタイプ**&#x200B;を使用することで、ビデオ訪問者を識別して、ビデオのコンバージョン率を計算できます。

* **a.media.timePlayed**
   * Variable type: Event
   * タイプ：カウンター
   * 前回のデータ収集プロセス（イメージリクエスト）以降のビデオ視聴秒数をカウントします。

* **a.media.view**
   * Variable type: Event
   * タイプ：カウンター
   * 訪問者がビデオの一部を視聴したことを示します。

      ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

* **a.media.segmentView**
   * Variable type: Event
   * タイプ：カウンター
   * 訪問者がビデオセグメントの一部を視聴したことを示します。

      ただし、訪問者がビデオを視聴した時間や視聴した部分に関する情報は提供されません。

* **a .media.complete**
   * Variable type: Event
   * タイプ：カウンター
   * ユーザーがビデオを最後まで視聴したことを示します。

      デフォルトでは、完了イベントはビデオが終了する 1 秒前に測定されます。実装時に、表示完了と見なすビデオの終わりからの秒数を指定できます。終了が定義されていないライブビデオやその他のストリーミングでは、完了を測定するカスタムポイントを指定できます（例えば、一定の時間視聴した後）。


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

ビデオの追跡に使用したい設定で `MediaSettings` オブジェクトを設定します。

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 例えば、プレーヤーが一時停止したときは、`mediaStop` を呼び出します。再生が開始または再開された場合は `mediaPlay` が呼び出されます。

## クラス {#section_16838332727348F990305C0C6B0D795C}

**クラス：MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**クラス：MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

Here are the methods in the Media Measurement class:

* **settingsWith**

   指定したパラメーターと共に `MediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   広告ビデオの追跡に使用する `MediaSettings` オブジェクトを返します。
   * このメソッドの構文を次に示します。

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   追跡用の `MediaSettings` オブジェクトを開きます。

   * このメソッドの構文を次に示します。

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      *name* という名前のメディアアイテムを閉じます。

      * このメソッドの構文を次に示します。
      ```java
      public static void close(String name);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.close("name"); 
      ```


* **play**
   * *name* という名前のメディアアイテムを、指定の *offset*（秒）で再生します。
   * このメソッドの構文を次に示します。

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **complete**

   指定されたメディアアイテムが指定の *offset*（秒）で再生完了されたことを手動で記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void complete(String name, double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   指定された *offset* でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void stop(String name, double offset); 
      ```

   * 次に、コードサンプルまたはこのメソッドを示します。

      ```java
      Media.stop("name", 0);
      ```

* **click**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```java
      public static void click(String name double offset); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.click("name", 0);
      ```

* **track**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Media.track("name", null); 
      ```
