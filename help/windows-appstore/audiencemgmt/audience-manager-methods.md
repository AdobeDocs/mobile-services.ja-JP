---
description: Windows 8.1ユニバーサルアプリストアライブラリが提供するAudience Managerメソッドのリスト。
seo-description: Windows 8.1ユニバーサルアプリストアライブラリが提供するAudience Managerメソッドのリスト。
seo-title: Audience Manager メソッド
solution: Marketing Cloud,Analytics
title: Audience Manager メソッド
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Audience Manager メソッド{#audience-manager-methods}

Windows 8.1ユニバーサルアプリストアライブラリが提供するAudience Managerメソッドのリスト。

SDKは、現在、Analytics、ターゲット、Audience Managerを含む複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Audience Managerメソッドの先頭には「AudienceManager」が付きます。

>[!NOTE]
>
>winJS (JavaScript)からwinmdメソッドを使用する場合、すべてのメソッドの最初の文字が自動的に小文字に変換されます。

オーディエンスマネージャーがJSONファイル内に設定されている場合は、ライフサイクルヒットと共に、ライフサイクル指標を含むシグナルが送信されます。

* **GetVisitorProfile (winJS:getVisitorProfile)**

   取得された最も直近の訪問者プロファイルを返します。Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * このメソッドの構文を次に示します。

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS:getDpid)**

   現在の DPID を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **GetDpuuid (winJS:getDpuuid)**

   現在の DPUUID を返します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid (winJS:setDpidAndDpuuid)**

   DPID および DPUUID を設定します。DPID と DPUUID が設定されている場合は、各シグナルと共に送信されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS:signalWithData)**

   特性を持つシグナルをAudience Managerに送信し、ブロックコールバックで返された一致するセグメントを取得します。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

