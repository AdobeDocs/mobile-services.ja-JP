---
description: Windows 8.1 ユニバーサルApp Storeライブラリが提供するAudience Managerメソッドの一覧です。
solution: Experience Cloud Services,Analytics
title: Audience Manager メソッド
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Audience Manager メソッド {#audience-manager-methods}

Windows 8.1 ユニバーサルApp Storeライブラリが提供するAudience Managerメソッドの一覧です。

SDK は現在、Analytics、Target、Audience Managerなど、複数のAdobe Experience Cloudソリューションをサポートしています。 メソッドには、ソリューションに応じたプレフィックスが付きます。Audience Managerメソッドの前には「AudienceManager」というプレフィックスが付きます。

>[!NOTE]
>
>winJS (JavaScript) から winmd メソッドを使用する場合、すべてのメソッドで最初の文字が自動的に小文字に変換されます。

JSON ファイル内で Audience Manager が設定されている場合は、ライフサイクル指標を含むシグナルがライフサイクルヒットと共に送信されます。

* **GetVisitorProfile (winJS:getVisitorProfile)**

   取得された最も直近の訪問者プロファイルを返します。戻り値 `null` （まだシグナルが送信されていない場合）。 訪問者プロファイルはに保存されます `SharedPreferences` を使用すると、複数回の起動時でも簡単にアクセスできます。

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

   Audience Managerに特性を持つシグナルを送信し、ブロック callback で返された一致するセグメントを取得します。

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
