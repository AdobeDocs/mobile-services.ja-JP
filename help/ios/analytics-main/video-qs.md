---
description: マイルストーンビデオ測定を使用した iOS でのビデオ測定に関する情報を以下に示します。
seo-description: マイルストーンビデオ測定を使用した iOS でのビデオ測定に関する情報を以下に示します。
seo-title: ビデオ分析
solution: Experience Cloud,Analytics
title: ビデオ分析
topic-fix: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
exl-id: d4d11ca0-1280-49db-8983-5b6d83856482
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 100%

---

# ビデオ分析 {#video-analytics}

マイルストーンビデオ測定を使用した iOS でのビデオ測定に関する情報を以下に示します。

>[!TIP]
>
>ビデオの再生中に、頻繁な「ハートビート」コールが送信され、再生時間を測定します。これらのハートビート呼び出しは、10 秒ごとに送信されるので、ビデオエンゲージメント指標やビデオフォールアウトレポートがより正確になります。詳しくは、「[Adobe Analytics でのオーディオとビデオの測定](https://docs.adobe.com/content/help/ja-JP/media-analytics/using/media-overview.html)」を参照してください。

ビデオを測定する一般的なプロセスは、どのプラットフォームでも同様です。ここでは、開発者タスクの基本的な概要とコードサンプルを提示します。

## プレーヤーイベントの Analytics 変数へのマッピング {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

次の表に、Analytics に送信されるメディアデータのリストを示します。処理ルールを使用して、コンテキストデータを Analytics 変数にマッピングします。

* **a.media.name**

   （必須）訪問者がビデオを何らかの方法で表示した場合に、実装で指定されているビデオの名前を収集します。この変数に分類を追加できます。

   （オプション）カスタムインサイト変数はビデオパス情報を提供します。

   * 変数型：eVar
   * デフォルトの有効期限：訪問
   * カスタムインサイト（s.prop、ビデオパスに使用）

* **a.media.name**

   （オプション）ビデオパス情報を提供します。この変数に対して、サポートでパスを有効にする必要があります。

   * 変数タイプ：カスタムインサイト（s.prop）
   * イベントタイプ：カスタムインサイト（s.prop）

* **a.media.segment**

   （必須）セグメント名や、ビデオ内でのセグメントの発生順序を含め、ビデオセグメントデータを収集します。この変数を入力するには、プレーヤーイベントを自動的に追跡する場合に `segmentByMilestones` 変数を有効にするか、プレーヤーイベントを手動で追跡する場合にカスタムセグメント名を設定します。例えば、訪問者がビデオの最初のセグメントを表示すると、SiteCatalyst によって `1:M:0-25` Segments eVar に次の情報が収集されます。

   デフォルトのビデオデータ収集方法では、次の時点でデータが収集されます。

   * ビデオ開始（再生）
   * セグメント開始
   * ビデオ終了（停止）

   Analytics は、訪問者開始が視聴しているときに、最初のセグメント表示をセグメントの開始でカウントします。後続のセグメントは、セグメントの開始時に表示されます。

   * 変数型：eVar
   * デフォルトの有効期限：ページビュー


* **a.contentType**

   訪問者によって閲覧されたコンテンツのタイプに関するデータを収集します。ビデオ測定によって送信されるヒットには、コンテンツタイプ `video` が割り当てられます。この変数は、ビデオ追跡専用に予約する必要はありません。同じ変数を使用する他のコンテンツレポートコンテンツタイプを使用することにより、異なるコンテンツのタイプでの訪問者の分布を分析できます。例えば、この変数を使用する「記事」や「製品ページ」などの値を使用して、他のコンテンツタイプにタグを付けることができます。ビデオ指標の見地からすると、コンテンツタイプを使用することで、ビデオ訪問者を識別して、ビデオのコンバージョン率を計算できます。

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

* **a.media.complete**

   ユーザーがビデオを最後まで視聴したことを示します。デフォルトでは、完了イベントはビデオが終了する 1 秒前に測定されます。導入時に、表示完了と見なすビデオの終わりからの秒数を指定できます。終わりが定義されていないライブビデオや他のストリームの場合は、カスタムポイントを指定して、例えば、特定の視聴後に完了を測定できます。

   * 変数型：イベント
   * タイプ：カウンター

## メディア設定の指定 {#section_929945D4183C428AAF3B983EFD3E2500}

ビデオの追跡に使用する設定で `ADBMediaSettings` オブジェクトを指定します。

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## プレーヤーイベントの追跡 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

ビデオの再生を測定するには、`mediaPlay`、`mediaStop` および `mediaClose` メソッドを適切なときに呼び出す必要があります。例えば、プレーヤーが一時停止した場合は `mediaStop` が呼び出され、再生が開始または再開された場合は `mediaPlay` が呼び出されます。

以下の例は、通知の設定と、ビデオを測定するメディアメソッドの呼び出しを示したものです。

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## クラス {#section_16838332727348F990305C0C6B0D795C}

### クラス：ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### クラス：ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## メディア測定クラスとメソッドのリファレンス {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   指定したパラメーターと共に `ADBMediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   広告ビデオの追跡に使用する `ADBMediaSettings` オブジェクトを返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   追跡する `ADBMediaSettings` オブジェクトを開きます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   *name* という名前のメディアアイテムを閉じます。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   指定された&#x200B;*名前*&#x200B;のメディアアイテムを指定された&#x200B;*オフセット*（秒）で再生したことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   指定された&#x200B;*オフセット*&#x200B;でメディアアイテムが再生完了されたことを手動で記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   指定された *offset* でビデオが停止または一時停止されたことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   メディアアイテムがクリックされたことを記録します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   現在のメディア状態をトラックアクション呼び出し（ページビューがカウントされない方式）で送信します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```
