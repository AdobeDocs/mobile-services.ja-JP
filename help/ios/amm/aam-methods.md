---
description: iOS ライブラリが提供する Audience Manager メソッドの一覧を以下に示します。
solution: Experience Cloud,Analytics
title: Audience Manager メソッド
topic-fix: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
exl-id: b843a52f-2b83-4e19-9f43-895bd582d4ef
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Audience Manager メソッド {#audience-manager-methods}

iOS ライブラリが提供する Audience Manager メソッドの一覧を以下に示します。

SDK は現在、Analytics、Target、Audience Manager、Adobe Experience Platform ID サービスなど、複数の Adobe Experience Cloud ソリューションをサポートしています。各メソッドには、ソリューションに応じたプレフィックスが付きます。Audience Manager メソッドの場合、プレフィックスは「`audience`」となります。

JSON ファイル内で Audience Manager が設定されている場合は、ライフサイクル指標を含むシグナルが `application:didFinishLaunchingWithOptions:` で送信されます。

* **audienceVisitorProfile**

   最後に取得した訪問者プロファイルを返します。シグナルが送信されていない場合は `null` を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`NSUserDefaults` に保存されます。

   * このメソッドの構文を次に示します。

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * このメニューのコードサンプルを次に示します。

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

   DPID および DPUUID を設定します。設定した場合、両方が各シグナルに追加されます。

   * **データプロバイダー ID（DPID）** は、Audience Manager によって割り当てられるデータパートナー ID です。
   * **データプロバイダーユニークユーザー ID（DPUUID）** は、ユーザーに対するデータプロバイダーの一意の ID です。

      >[!IMPORTANT]
      >
      >4.13.x より前のバージョンでは、DPUUID は自動的にエンコードされませんでした。バージョン 4.13.x 以降、SDK は、渡された値のエンコードを最初に解除し、次にこの値を再エンコードします。このプロセスは、SDK の後方互換性が損なわれないようにします。

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
