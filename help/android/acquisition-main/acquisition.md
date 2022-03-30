---
description: Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。
keywords: Android, ライブラリ, モバイル, SDK
solution: Experience Cloud Services,Analytics
title: モバイルアプリの獲得
topic-fix: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
exl-id: 266f0266-38f5-410b-ae14-92874fb0e7ce
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 100%

---

# モバイルアプリの獲得 {#mobile-app-acquisition}

Adobe Mobile Services で一意のトラッキングコードを持つダウンロード計測用リンクを生成できます。生成されたリンクをユーザーがクリックした後で App Store からアプリをダウンロードして実行すると、SDK が自動的に獲得データを収集し、Adobe Mobile Services に送信します。

## 新しい Adobe Experience Platform Mobile SDK リリース

Adobe Experience Platform Mobile SDK に関する情報やドキュメントをお探しの場合[こちら](https://aep-sdks.gitbook.io/docs/)をクリックし、最新のドキュメントを参照してください。

2018 年 9 月に、SDK の新しいメジャーバージョンをリリースしました。これらの新しい Adobe Experience Platform Mobile SDK は、[Experience Platform Launch](https://www.adobe.com/jp/experience-platform/launch.html) から設定できます。

* 開始するには、Adobe Experience Platform Launch に移動します。
* Experience Platform SDK リポジトリの内容については、[Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks) を参照してください。

>[!IMPORTANT]
>
>獲得を使用するには、SDK バージョン 4.1 以降が&#x200B;**必要**&#x200B;です。

ダウンロード計測用リンクは、Adobe Mobile Services で作成する必要があります。詳しくは、「[獲得](/help/using/acquisition-main/acquisition-main.md)」を参照してください。

**SDK バージョン 4.18.0 以降**：

2020 年 3 月 1 日以降、Google は install_referrer インテントブロードキャストメカニズムを廃止します。詳しくは、「[まだ InstallBroadcast を使用している場合は、2020 年 3 月 1 日までに再生リファラー API に切り替えてください](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)」を参照してください。Google Play ストアから引き続きインストールリファラー情報を収集するには、SDK バージョン 4.18.0 以降を使用するようにアプリケーションを更新します。

廃止に伴い、`BroadcastReceiver` を作成する代わりに、新しい Google API からインストールリファラー URL を収集し、その URL を SDK に渡す必要があります。

1. Google Play インストールリファラーパッケージをグレードファイルの依存関係に追加します。

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. インストールリファラー API からリファラー URL を取得するには、[インストールリファラーの取得](https://developer.android.com/google/play/installreferrer/library#install-referrer)の手順を実行します。

1. リファラー URL を SDK に渡します。

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>アプリケーションで不要な API 呼び出しがおこなわれるのを避けるために、Google ではインストール直後に 1 回だけ API を呼び出すことをお勧めします。

アプリで Google Play インストールリファラー API を使用する最善の方法を決定するには、Google のドキュメントを参照してください。Google Play インストールリファラー API での Adobe SDK の使用方法の例を次に示します。

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**SDK バージョン 4.13.1 以降**：

Adobe Mobile Services で作成されたダウンロード計測用リンクを使用できない場合でも、Google Play Acquisition を使用して、SDK で獲得データを収集し、送信することができます。

標準の Google Play Acquisition キャンペーンから獲得データを収集するには：

* 標準の Google Play ストアの獲得方法を使用します。

   カスタム獲得データは、標準の Google Play Acquisition のキーと値のペアで使用できます。

* ユーザーが Google Play ストアの獲得の結果としてアプリをダウンロードして実行すると、リファラーからのデータが収集され、Adobe Mobile Services に送信されます。

   * データは保存され、以前に SDK に登録された `AdobeDataCallback` インスタンスで使用できます。

      詳しくは、「[設定メソッド](/help/android/configuration/methods.md)」を参照してください。

   * `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` または `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` イベントタイプが使用されます。

   * Google Play の獲得データに含まれていたカスタムキーには、「`a.acquisition.custom.`」という名前空間が設定されます。

Adobe Mobile Services で作成されたダウンロード計測用リンクを使用している場合は、次のタスクを実行して、カスタムデータをダウンロード計測用リンクに追加します。

1. 獲得変数の先頭にプレフィックス「`adb`」を付けます。

   初回起動時に SDK が Adobe Mobile Services から獲得データを受け取ると、データが保存され、SDK で以前登録された `AdobeDataCallback` インスタンスでそのデータを使用できるようになります。詳しくは、「[設定メソッド](/help/android/configuration/methods.md)」を参照してください。

1. `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` または `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` イベントタイプが使用されます。

1. カスタムデータキーには、「`a.acquisition.custom.`」というプレフィックスが付けられます。

>[!TIP]
>
>複数のレポートスイートにデータを送信する場合は、レポートスイート ID のリストの最初のレポートスイートに関連付けられているアプリの獲得データを使用します。

このセクションの更新により、SDK はダウンロード計測用リンクから獲得データを送信できます。

## モバイルの獲得の追跡 {#section_CEA30C652AC8470784B8054E299B80FA}

1. ライブラリをプロジェクトに追加し、ライフサイクルを実装します。

   詳しくは、[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)の「*IntelliJ IDEA または Eclipse プロジェクトへの SDK と設定ファイルの追加*」を参照してください。

1. ライブラリをインポートします。

   ```java
   import com.adobe.mobile.*;
   ```

1. リファラーの `BroadcastReceiver` を実装します。

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. `AndroidManifest.xml` を更新して、前の手順で作成した `BroadcastReceiver` を有効にします。

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. `ADBMobileConfig.json` ファイルに次の必須の acquisition 設定が含まれていることを確認します。

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   > データを複数のレポートスイートに送信する場合は、レポートスイート ID のリスト内の最初のレポートスイートに関連付けられたアプリの獲得設定（獲得サーバーと appid）を使用してください。

   `acquisition` 設定は Adobe Mobile Services によって生成されます。この設定を変更しないでください。`acquisition` 設定が事前に設定されているカスタマイズ済みの `ADBMobileConfig.json` ファイルをダウンロードする方法について詳しくは、「[事前準備](/help/android/getting-started/requirements.md)」を参照してください。

これらの設定を有効にすると、アプリを初めて起動した後、最初のライフサイクル呼び出しで獲得データが自動的に送信されます。

>[!CAUTION]
>
>`referrerTimeout`アプリの獲得を有効にするには、 を 0 より大きい値に設定する必要があります。
