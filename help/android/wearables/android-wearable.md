---
description: Android SDK バージョン 4.5 から新しい Android 拡張機能が追加され、Android ウェアラブルアプリからデータを収集できるようになりました。
seo-description: Android SDK バージョン 4.5 から新しい Android 拡張機能が追加され、Android ウェアラブルアプリからデータを収集できるようになりました。
seo-title: Android Wearablesはじめに
solution: Marketing Cloud,Analytics
title: Android Wearables  Getting Started
topic: 開発者と導入
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: getting started{#android-wearables-getting-started}

Android SDK バージョン 4.5 から新しい Android 拡張機能が追加され、Android ウェアラブルアプリからデータを収集できるようになりました。

## Configuring the SDK for a handheld app (Android Studio) {#section_262237484EC44C58953891B105F0D000}

For more information about importing the SDK into your project, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)

1. `ADBMobileConfig.json` ファイルをプロジェクトの assets フォルダーに追加します。
1. `adobeMobileLibrary-*.jar` ファイルを libs フォルダーに追加するか、このファイルをプロジェクトで参照されるように設定します。

   >[!TIP]
   >
   >You might need to sync the gradle project after adding the `.jar` file.

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

1. Add the following code to the `AndroidManifest.xml` file:

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
1. Implement `WearableListenerService` or add the corresponding code to your `WearableListenerService`:

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

1. Add  to the  file:`WearListenerService``AndroidManifest.xml`

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

## Configuring the SDK for a Wearable app (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

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
1. Implement `WearableListenerService` or add the corresponding code to your `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Add  to the  file:`WearListenerService``AndroidManifest.xml`

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

