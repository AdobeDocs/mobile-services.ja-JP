---
product: mobile-services
audience: end-user
user-guide-title: Mobile Services Androidヘルプ
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android Help{#android}

+ [Experience Cloud ソリューション用 Android SDK 4.x](overview.md)
+ [リリースノート](rel-notes.md)
+ はじめに{#getting-started-android}
   + [はじめに](getting-started/getting-started.md)
   + [始める前に](getting-started/requirements.md)
   + [コアの実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ](getting-started/proc-rules.md)
   + [Android 4.x ライブラリへの移行](getting-started/migration-v3.md)
+ 設定{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config file](configuration/json-config/json-config.md)
   + [Override the ADBMobile JSON config path](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定方法](configuration/methods.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュを追跡](analytics-main/crashes.md)
   + [Timed actions](analytics-main/timed-actions.md)
   + [訪問者の全期間値](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [製品変数](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [Event serialization](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック{#postbacks}
      + [ポストバックの概要](analytics-main/postbacks/postbacks.md)
      + [ポストバックの例](analytics-main/postbacks/postback-example.md)
      + [PII ポストバック](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analyticsメソッド](analytics-main/analytics-methods.md)
+ 獲得{#acquisition-android}
   + [獲得の概要](acquisition-main/acquisition-main-android.md)
   + [Mobile app acquisition](acquisition-main/acquisition.md)
   + [Acquisition methods](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティの遅延ディープリンクの追跡](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [マーケティングリンク獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3獲得のテスト](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testing legacy acquisition](acquisition-main/t-testing-acquisition.md)
   + [Troubleshoot Acquisition testing](acquisition-main/troubleshoot-acquisition-testing.md)
+ メッセージ{#messaging-android}
   + [Messaging overview](messaging-main/messaging-main-android.md)
   + アプリ内メッセージ{#inapp-messaging}
      + [アプリ内メッセージ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [リッチプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 場所{#location}
   + [場所の概要](location/location.md)
   + [地域と目標地点](location/geo-poi.md)
   + [ビーコン追跡](location/beacon.md)
+ Target{#target-android}
   + [Target overview](target-main/target-main.md)
   + [ターゲット設定](target-main/target.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [Android でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-android.md)
   + [Android の Target プレビュー](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience cloudの概要](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud IDの設定](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform IDサービスのメソッド](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Managerの概要](audience-manager/audience-manager.md)
   + [Audience Managerの設定](audience-manager/audiencemgmt.md)
   + [Audience Manager methods](audience-manager/c-audience-manager-methods.md)
+ ウェアラブル{#wearables-android}
   + [Wearables overview](wearables/wearables.md)
   + [Android Wearables:はじめに](wearables/android-wearable.md)
   + [Android Wearables:追加メモ](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK reference overview](/help/android/reference/reference.md)
   + [アプリ ID](/help/android/reference/app-ids.md)
   + [アプリとモバイルWeb間の訪問者の追跡](/help/android/reference/hybrid-app.md)
   + [Androidウィジェット](/help/android/reference/widgets.md)
+ プライバシーと一般データ保護規則{#gdpr-privacy-android}
   + [Privacy and GDPR overview](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Retrieving stored identifiers](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap プラグイン{#phonegap-android}
   + [PhoneGap plug-in overview](phonegap/phonegap.md)
   + [PhoneGap plug-in methods](phonegap/phonegap-methods.md)
