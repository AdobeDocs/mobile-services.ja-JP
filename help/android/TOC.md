---
audience: end-user
user-guide-title: Mobile Services Android ガイド
breadcrumb-title: Android ガイド
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 99%

---


# Mobile Services Android ガイド{#android}

+ [Experience Cloud ソリューション用 Android SDK 4.x](overview.md)
+ [リリースノート](rel-notes.md)
+ はじめに {#getting-started-android}
   + [はじめに](getting-started/getting-started.md)
   + [事前準備](getting-started/requirements.md)
   + [コア実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ ](getting-started/proc-rules.md)
   + [Android 4.x ライブラリへの移行](getting-started/migration-v3.md)
+ 設定 {#configuration-android}
   + [設定の概要](configuration/configuration.md)
   + [ADBMobile JSON 設定ファイル](configuration/json-config/json-config.md)
   + [ADBMobile JSON 設定パスのオーバーライド](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定メソッド](configuration/methods.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics {#analytics-android}
   + [Analytics の概要](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュの追跡](analytics-main/crashes.md)
   + [時間計測アクション](analytics-main/timed-actions.md)
   + [訪問者のライフタイム値](analytics-main/lifetime-value.md)
   + products 変数 {#products-variable}
      + [products 変数](analytics-main/products/products.md)
      + [マーチャンダイジング eVar および製品固有のイベントを持つ products 変数](analytics-main/products/products-variable-evars-events.md)
   + [イベントのシリアル化](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック {#postbacks}
      + [ポストバックの概要](analytics-main/postbacks/postbacks.md)
      + [ポストバックの例](analytics-main/postbacks/postback-example.md)
      + [PII ポストバック](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analytics メソッド](analytics-main/analytics-methods.md)
+ 獲得 {#acquisition-android}
   + [獲得の概要](acquisition-main/acquisition-main-android.md)
   + [モバイルアプリの獲得](acquisition-main/acquisition.md)
   + [獲得メソッド](acquisition-main/acquisition-methods.md)
   + ディープリンクの追跡 {#tracking-deep-links}
      + [ディープリンクの追跡](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティのディファードディープリンクの追跡](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [マーケティングリンクによる獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3 による獲得のテスト ](acquisition-main/t-testing-version-3-acquisition.md)
   + [従来の獲得のテスト](acquisition-main/t-testing-acquisition.md)
   + [獲得テストのトラブルシューティング](acquisition-main/troubleshoot-acquisition-testing.md)
+ メッセージ {#messaging-android}
   + [メッセージの概要](messaging-main/messaging-main-android.md)
   + アプリ内メッセージ {#inapp-messaging}
      + [アプリ内メッセージ ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング ](messaging-main/messaging/in-apps-ts.md)
   + プッシュメッセージ {#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [ディープリンクを使用したプッシュメッセージの実装](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [リッチプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ ロケーション {#location}
   + [ロケーションの概要](location/location.md)
   + [位置情報と目標地点](location/geo-poi.md)
   + [ビーコントラッキング](location/beacon.md)
+ Target {#target-android}
   + [Target の概要](target-main/target-main.md)
   + [Target の設定](target-main/target.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [Android でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-android.md)
   + [Android の Target プレビュー](target-main/c-mob-target-preview-android.md)
+ Experience Cloud {#experience-cloud-android}
   + [Experience Cloud の概要](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID の設定](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform ID サービスのメソッド](c-marketing-cloud/mc-methods.md)
+ Audience Manager {#audience-manager-android}
   + [Audience Manager の概要](audience-manager/audience-manager.md)
   + [Audience Manager の設定](audience-manager/audiencemgmt.md)
   + [Audience Manager メソッド](audience-manager/c-audience-manager-methods.md)
+ ウェアラブル {#wearables-android}
   + [ウェアラブルの概要](wearables/wearables.md)
   + [Android ウェアラブル：はじめに ](wearables/android-wearable.md)
   + [Android ウェアラブル：追加の注意事項 ](wearables/c-android-wearables--additional-notes.md)
+ Android SDK リファレンス {#sdk-reference-android}
   + [Android SDK リファレンスの概要](/help/android/reference/reference.md)
   + [アプリ ID](/help/android/reference/app-ids.md)
   + [アプリとモバイル Web にまたがる訪問者トラッキング ](/help/android/reference/hybrid-app.md)
   + [Android ウィジェット](/help/android/reference/widgets.md)
+ プライバシーと一般データ保護規則 {#gdpr-privacy-android}
   + [プライバシーと GDPR の概要](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [保存されている ID の取得](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap プラグイン {#phonegap-android}
   + [PhoneGap プラグインの概要](phonegap/phonegap.md)
   + [PhoneGap プラグインのメソッド](phonegap/phonegap-methods.md)
