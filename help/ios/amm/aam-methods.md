---
description: iOS ライブラリが提供する Audience Manager メソッドの一覧を以下に示します。
seo-description: iOS ライブラリが提供する Audience Manager メソッドの一覧を以下に示します。
seo-title: Audience Manager メソッド
solution: Marketing Cloud、Analytics
title: Audience Manager メソッド
topic: 開発者と導入
uuid: 97658bd6-4c4f-4875- aba9-36family4ec8bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

iOS ライブラリが提供する Audience Manager メソッドの一覧を以下に示します。

SDKは、現在、Analytics、Target、Audience Manager、Adobe Experience Platform IDサービスを含む複数のAdobe Experience Cloudソリューションをサポートしています。各メソッドには、ソリューションに応じたプレフィックスが付きます。 Manager メソッドの場合、プレフィックスは「`audience`audience」となります。

JSON ファイル内で Audience Manager が設定されている場合は、ライフサイクル指標を含むシグナルが `application:didFinishLaunchingWithOptions:` : で送信されます。

* **audienceVisitorProfile**

   最後に取得した訪問者プロファイルを返します。シグナルが送信されていない場合は `null` を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`NSUserDefaults` に保存されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * 以下に、このメニューのコードサンプルを示します。

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   現在の DPID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   現在の DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   DPID および DPUUID を設定します。設定すると、両方が各シグナルに追加されます。

   * **データプロバイダー ID（DPID）**&#x200B;は、Audience Manager によって割り当てられるデータパートナー ID です。
   * **データプロバイダー個別ユーザー ID（DPUUID）**&#x200B;は、データプロバイダーにおける一意のユーザー ID です。

      >[!IMPORTANT]
      >
      >バージョン4.13以前は、DPUUIDは自動的にエンコードされませんでした。バージョン 4.13.x 以降の SDK は、渡された値のエンコードを解除してから、この値を再エンコードします。このプロセスにより、後方互換性が確保されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Audience Manager UUID をリセットし、現在の訪問者プロファイルを削除します。

   * このメソッドの構文を次に示します。

      ```objective-c
      +(void) audienceReset;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   特性を持つシグナルを Audience Management に送信し、ブロック callback に返された一致するセグメントを取得します。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## 例

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
