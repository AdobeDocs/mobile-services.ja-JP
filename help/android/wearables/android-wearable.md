---
description: Android SDK バージョン 4.5 から新しい Android 拡張機能が追加され、Android ウェアラブルアプリからデータを収集できるようになりました。
solution: Experience Cloud,Analytics
title: Android ウェアラブル：はじめに
topic-fix: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
exl-id: 79cfaa48-d9b2-4518-8b31-d7041898a71b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 100%

---

# Android ウェアラブル：はじめに {#android-wearables-getting-started}

Android SDK バージョン 4.5 から新しい Android 拡張機能が追加され、Android ウェアラブルアプリからデータを収集できるようになりました。

## ハンドヘルドアプリ用の SDK の設定（Android Studio）  {#section_262237484EC44C58953891B105F0D000}

SDK をプロジェクトに読み込む方法について詳しくは、「[コア実装とライフサイクル](/help/android/getting-started/dev-qs.md)」を参照してください。

1. `ADBMobileConfig.json` ファイルをプロジェクトの assets フォルダーに追加します。
1. `adobeMobileLibrary-*.jar` ファイルを libs フォルダーに追加するか、このファイルをプロジェクトで参照されるように設定します。

   >[!TIP]
   >
   >`.jar` ファイルを追加した後で gradle プロジェクトを同期することが必要になる場合があります。

1. `onCreate` メソッドで、`Config.setContext` を使用して SDK がアプリケーションコンテキストにアクセスできるようにします。

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. `AndroidManifest.xml` ファイルに次のコードを追加します。

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. プロジェクトに Google Play サービスライブラリが含まれていることを確認します。
1. `WearableListenerService` を実装するか、対応するコードを `WearableListenerService` に追加します。

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. `AndroidManifest.xml` ファイルに `WearListenerService` を追加します。

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## ウェアラブルアプリ用の SDK の設定（Android Studio）  {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. 次のどちらかのタスクを実行します。

   * `ADBMobileConfig.json` ファイルをウェアラブルプロジェクトの assets フォルダーに追加します。
   * ハンドヘルドアプリの assets フォルダーにある `ADBMobileConfig.json` を使用するように gradle 設定を変更します。

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. `adobeMobileLibrary-*.jar` ファイルを libs フォルダーに追加するか、プロジェクトで参照されるように設定します。

   jar ファイルを追加した後で gradle プロジェクトを同期することが必要になる場合があります。

1. `onCreate` メソッドで、`Config.setContext` を使用して SDK がアプリケーションコンテキストにアクセスできるようにします。

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. 次のコードを `AndroidManifest.xml` に追加します。

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. プロジェクトに Google Play サービスライブラリが含まれていることを確認します。
1. `WearableListenerService` を実装するか、対応するコードを `WearableListenerService` に追加します。

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. `AndroidManifest.xml` ファイルに `WearListenerService` を追加します。

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```
