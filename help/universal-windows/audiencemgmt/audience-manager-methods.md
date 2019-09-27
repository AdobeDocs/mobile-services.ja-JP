---
description: Universal Windows Platform ライブラリで提供されている Audience Manager メソッドのリストです。
seo-description: Universal Windows Platform ライブラリで提供されている Audience Manager メソッドのリストです。
seo-title: Audience Manager methods
solution: Marketing Cloud,Analytics
title: Audience Manager methods
topic: 開発者と導入
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

Universal Windows Platform ライブラリで提供されている Audience Manager メソッドのリストです。

現在、SDK では、Analytics、Target、Audience Manager をはじめとする複数の Adobe Experience Cloud ソリューションがサポートさています。メソッドには、ソリューションに応じたプレフィックスが付きます。Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

If audience manager is configured in your JSON file, a signal that contains lifecycle metrics is sent in with your lifecycle hit.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   取得された最も直近の訪問者プロファイルを返します。まだシグナルが送信されていない場合は `null` を返します。訪問者プロファイルは、次回以降のアプリ起動時も簡単にアクセスできるように、`SharedPreferences` に保存されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

* **GetDpuuid (winJS: getDpuuid)**

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

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   DPID および DPUUID を設定します。DPID および DPUUID が設定されている場合、各シグナルと共に送信されます。

   * このメソッドの構文を次に示します。

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Audience Management に特性を持つシグナルを送信し、ブロックコールバックで返された一致するセグメントを取得します。

   * このメソッドの構文を次に示します。

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      
