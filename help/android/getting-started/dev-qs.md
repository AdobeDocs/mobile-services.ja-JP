---
description: この情報は、Android ライブラリを実装し、ライフサイクル指標（起動、アップグレード、セッション、アクションを実行したユーザーなど）を収集する場合に役立ちます。
keywords: android;library;mobile;sdk
seo-description: この情報は、Android ライブラリを実装し、ライフサイクル指標（起動、アップグレード、セッション、アクションを実行したユーザーなど）を収集する場合に役立ちます。
seo-title: コア実装とライフサイクル
solution: Marketing Cloud,Analytics
title: コア実装とライフサイクル
topic: 開発者と導入
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbb2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

この情報は、Android ライブラリを実装し、ライフサイクル指標（起動、アップグレード、セッション、アクションを実行したユーザーなど）を収集する場合に役立ちます。

## SDK のダウンロード {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>SDKをダウンロードするには、Android 2.2以降を使用する必要があります。

1. 以下の節に示す手順を実行して、開発レポートスイートを設定し、事前に構成された設定ファイルをダウンロードします。

   * [レポートスイートの作成](/help/android/getting-started/requirements.md)
   * [SDK のダウンロード](/help/android/getting-started/requirements.md)

1. ファイルをダウンロードして解凍し `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` 、次のソフトウェアコンポーネントが存在することを確認します。

   * `adobeMobileLibrary.jar`Androidデバイスおよびシミュレーターで使用されるライブラリです。

   * `ADBMobileConfig.json`：アプリ用にカスタマイズされた SDK 設定ファイル。
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEAプロジェクト**

SDK と設定ファイルをプロジェクトに追加するには、以下のようにします。

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. プロジェクトナビゲーションパネルで、プロジェクトを右クリックします。
1. Select **[!UICONTROL Open Module Settings]**.
1. Under **[!UICONTROL Project Settings]**, select **[!UICONTROL Libraries]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. 「**[!UICONTROL Java]**」を選択し、`adobeMobileLibrary.jar` ファイルに移動します。
1. モバイルライブラリを使用する予定のモジュールを選択します。
1. 「**[!UICONTROL 適用]**」をクリックしてから「**[!UICONTROL OK]」をクリックして、モジュール設定ウィンドウを閉じます。**

**Eclipseプロジェクト**

SDK と設定ファイルをプロジェクトに追加するには、以下のようにします。

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. **[!UICONTROL Eclipse IDE]**&#x200B;で、プロジェクト名を右クリックします。
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. Select `adobeMobileLibrary.jar`.
1. Click **[!UICONTROL Open]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. 「**[!UICONTROL Order and Export（並べ替えとエクスポート）]**」タブで、**`adobeMobileLibrary.jar`が選択されていることを確認します。**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

AppMeasurement ライブラリでは、データの送信とオフラインのトラッキングコールの記録のために、次の権限が必要です。

* `INTERNET`
* `ACCESS_NETWORK_STATE`

これらの権限を追加するには、アプリケーションのプロジェクトディレクトリにある `AndroidManifest.xml` ファイルに以下の行を追加します。

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

メインアクティビティのメソッドに次のコ `onCreate` ードを追加する必要があります。

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

ライフサイクルを有効にすると、アプリが起動されるたびに、1 件のヒットが送信されて、起動、アップグレード、セッション、アクションを実行したユーザー、その他の多くの指標が測定されます。詳しくは、 [ライフサイクル指標](/help/android/metrics.md).

**アプリケーションの各アクティビティで次の手順を実行します。**

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. `onResume` 関数で、ライフサイクルデータの収集を開始します。

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. `onPause` 関数で、ライフサイクルデータの収集を一時停止します。

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>正確なクラッシュレポートを確実に作成するには、これらの呼び出しをすべてのアクティビティに追加する必要があります。 詳しくは、「アプリのクラッシュを追 [跡」を参照してください](/help/android/analytics-main/crashes.md)。

## ライフサイクル呼び出しに追加のデータを含める

追加のデータをライフサイクル指標呼び出しで含めるには、コンテキストデータを含む追加のパラメーターを `collectLifecycleData` に渡します。

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

`collectLifecycleData` で送信される追加のコンテキストデータ値は、Adobe Mobile Services のカスタム変数にマッピングする必要があります。

![](assets/map-variable-lifecycle.png)

その他のライフサイクル指標は自動的に収集されます。詳しくは、 [ライフサイクル指標](/help/android/metrics.md).

## 次の作業 {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

次のタスクを実行します。

* [アプリの状態の追跡](/help/android/analytics-main/states.md)
* [アプリのアクションの追跡](/help/android/analytics-main/actions.md)

