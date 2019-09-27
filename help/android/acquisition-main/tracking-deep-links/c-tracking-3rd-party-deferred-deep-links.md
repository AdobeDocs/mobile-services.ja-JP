---
description: Android SDK を使用して、サードパーティのディファードディープリンクの追跡を実装します。
seo-description: Android SDK を使用して、サードパーティのディファードディープリンクの追跡を実装します。
seo-title: サードパーティのディファードディープリンクの追跡
title: サードパーティのディファードディープリンクの追跡
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Tracking third-party deferred deep links{#tracking-third-party-deferred-deep-links}

Android SDK を使用して、サードパーティのディファードディープリンクの追跡を実装します。

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

現在、Adobe Mobile SDK では、ディープリンクをサポートしています。アプリ開発者は、ディープリンクされたアクティビティから `collectLifecycleData` SDK API を使用する必要があります。SDK は、ディープリンク URL パラメーターからディープリンクデータを追加します。Adobe Mobile SDK でのディープリンクの機能について詳しくは、 [ディープリンクの追跡](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

広告作成者は、Facebook 上に広告をディープリンクとして作成することができます。ユーザーが広告をクリックすると、ユーザーが関心を持っている情報にアプリ内で直接移動します。ディープリンクはフィンガープリンターの URL **ではありません**。ただし、広告の設定時にサードパーティのディープリンク URL を指定するオプションがあります。Adobe Mobile SDK および Services を使用しているアプリ開発者は、このフィールドに Adobe Mobile Services によって設定されたフィンガープリンターの URL を入力する必要があります。すべてが正しく設定されている場合、Facebook SDK は、アプリがインストールまたは起動されたときにこの URL をアプリケーションに渡します。

## SDK の設定 {#section_834CD3109175432B8173ECB6EA7DE315}

Adobe Mobile SDK によって Facebook ディープリンクのサポートを追加する準備をするには、アプリ開発者は以下のタスクを完了します。

* Android SDKの概要

   For more information, see [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) .

* ディープリンクの設定

   詳しくは、ディープリンクの設 [定を参照してください](https://developers.facebook.com/docs/app-ads/deep-linking#os)。

If the application is set up correctly, the `trackAdobeDeepLink()` API should enable collecting the deep link information from the Facebook acquisition campaign and send it to Adobe Mobile Service. 最初の起動時にインストールヒットが Adobe Mobile Service に送信されなかった場合、この情報はライフサイクルヒットに追加されます。それ以外の場合は、アドビディープリンクヒットとして送信されます。

>[!TIP]
>
>Ensure that the deep link URL has a key called `a.deeplink.id`. URL にディープリンク ID パラメーターがない場合、URL パラメーターはコンテキストデータに追加されません。

リンクが獲得に起因する可能性がある場合、Adobe Mobile SDK は、`trackAdobeDeepLink()` () を呼び出すために使用された Facebook ディープリンクからの獲得データを保存します。このデータは、将来の Adobe Mobile SDK リリースで使用できます。コールバックが登録されている場合は、データをクライアントに送り返すためにアドビコールバックも使用されます。

## Enable deep linking in an Android application {#section_64C15E269E89424B8E3D029F88094620}

1. ディープリンクを処理するアプリケーションを登録します。

   詳しくは、[他のアプリからのアクティビティの開始を許可する](https://developer.android.com/training/basics/intents/filters.html)を参照してください。

1. Facebook SDK をリンクします。

   アプリに Facebook gradle 依存関係を追加するには、[Android SDK スタートガイド](https://developers.facebook.com/docs/android/getting-started)の手順を実行します。

1. *Android Studio のセットアップ*&#x200B;節の手順を実行して、Facebook SDK を初期化します。
1. メインアクティビティから `trackAdobeDeepLink()` を呼び出します。

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

