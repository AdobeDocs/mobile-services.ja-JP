---
product: mobile-services
audience: end-user
user-guide-title: Mobile Services iOS ガイド
breadcrumb-title: iOS Guide
translation-type: ht
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: ht
source-wordcount: '286'
ht-degree: 100%

---


# Mobile Services iOS ガイド {#ios}

+ [Experience Cloud ソリューション用 iOS SDK 4.x](overview.md)
+ [リリースノート](rel-notes.md)
+ はじめに {#getting-started-ios}
   + [導入の概要](getting-started/getting-started.md)
   + [事前準備](getting-started/requirements.md)
   + [コア実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ](getting-started/proc-rules.md)
   + [Swift 統合 ](getting-started/swift-integration.md)
   + [4.x iOS ライブラリへの移行](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [設定の概要](configuration/configuration.md)
   + [ADBMobile JSON 設定](configuration/json-config/json-config.md)
   + [ADBMobile JSON 設定パスのオーバーライド](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定メソッド](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics の概要](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュの追跡](analytics-main/crashes.md)
   + [時間計測アクション](analytics-main/timed-actions.md)
   + [訪問者のライフタイム値](analytics-main/lifetime-value.md)
   + products 変数 {#products-variable}
      + [products 変数](analytics-main/products/products.md)
      + [マーチャンダイジング eVar および製品固有のイベントを持つ products 変数 ](analytics-main/products/products-variable-evars-events.md)
   + [イベントのシリアル化](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック {#postbacks}
      + [ポストバックの概要](analytics-main/postback/postback.md)
      + [ポストバックのサンプル ](analytics-main/postback/postback-example.md)
      + [PII ポストバック](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics メソッド](analytics-main/analytics-methods.md)
+ 獲得 {#acquisition-ios}
   + [獲得の概要](acquisition-main/acquisition-main.md)
   + [モバイルアプリの獲得](acquisition-main/acquisition.md)
   + [獲得メソッド](acquisition-main/c-acquisition-methods.md)
   + ディープリンクの追跡 {#tracking-deep-links}
      + [ディープリンクの追跡](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティのディファードディープリンクの追跡](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [マーケティングリンクによる獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3 による獲得のテスト](acquisition-main/t-testing-version-3-acquisition.md)
   + [従来の獲得のテスト](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ メッセージ {#messaging-ios}
   + [メッセージの概要](messaging-main/messaging-main.md)
   + アプリ内メッセージ {#in-app-messaging}
      + [アプリ内メッセージ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング](messaging-main/messaging/in-apps-ts.md)
   + プッシュメッセージ {#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [ディープリンクを使用したプッシュメッセージの実装](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [リッチプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ ロケーション {#location-ios}
   + [ロケーションの概要](location/location.md)
   + [位置情報と目標地点](location/geo-poi.md)
   + [iBeacon トラッキング](location/ibeacon.md)
+ Target {#target-ios}
   + [Target の概要](target-main/target-main.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [iOS でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-ios.md)
   + [iOS の Target プレビュー](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud の概要](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform ID サービスのメソッド](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager メソッド](amm/aam-methods.md)
+ tvOS を使用した Apple TV 実装 {#apple-tv-implementation-tvos-ios}
   + [tvOS を使用した Apple TV 実装](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [TVML／TVJS 対応の Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS メソッド](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS エクステンション実装 {#ios-ext}
   + [iOS エクステンション実装](ios-ext/ios-ext.md)
   + [スタンドアロンエクステンション実装](ios-ext/c-stand-alone-extension-implementation.md)
+ [WatchOS 2 を使用した Apple Watch 実装](apple-watch-implementation-watchkit.md)
+ iOS SDK リファレンス {#sdk-reference-ios}
   + [iOS SDK リファレンス ](reference/reference.md)
   + [アプリ ID](reference/app-ids.md)
   + [アプリとモバイル Web にまたがる訪問者トラッキング](reference/hybrid-app.md)
   + [iOS デバイスのバージョン](reference/device-versions.md)
+ プライバシーと一般データ保護規則 {#privacy-gdpr-ios}
   + [プライバシーと一般データ保護規則](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [保存されている ID の取得](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap プラグイン {#phonegap-ios}
   + [PhoneGap プラグイン](phonegap/phonegap.md)
   + [PhoneGap プラグインのメソッド ](phonegap/phonegap-methods.md)
