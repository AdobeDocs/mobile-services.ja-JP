---
product: モバイルサービス
audience: end-user
user-guide-title: Mobile Services iOSヘルプ
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOSヘルプ {#ios}

+ [Experience Cloud ソリューション用 iOS SDK 4.x](overview.md)
+ [リリースノート](rel-notes.md)
+ はじめに {#getting-started-ios}
   + [はじめにの概要](getting-started/getting-started.md)
   + [Before you start](getting-started/requirements.md)
   + [コアの実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ](getting-started/proc-rules.md)
   + [迅速な統合](getting-started/swift-integration.md)
   + [4.x iOSライブラリへの移行](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [ADBMobile JSON設定パスの上書き](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics {#analytics-ios}
   + [解析の概要](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュを追跡](analytics-main/crashes.md)
   + [Timed actions](analytics-main/timed-actions.md)
   + [訪問者の全期間値](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [製品変数](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [イベントシリアル化](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック {#postbacks}
      + [ポストバックの概要](analytics-main/postback/postback.md)
      + [ポストバックの例](analytics-main/postback/postback-example.md)
      + [PIIポストバック](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics methods](analytics-main/analytics-methods.md)
+ 獲得 {#acquisition-ios}
   + [獲得の概要](acquisition-main/acquisition-main.md)
   + [Mobile app acquisition](acquisition-main/acquisition.md)
   + [獲得方法](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティの遅延ディープリンクの追跡](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [マーケティングリンク獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3獲得のテスト](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testing legacy acquisition](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ メッセージ {#messaging-ios}
   + [Messaging overview](messaging-main/messaging-main.md)
   + アプリ内メッセージ {#in-app-messaging}
      + [アプリ内メッセージ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [リッチプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 場所 {#location-ios}
   + [場所の概要](location/location.md)
   + [地域と目標地点](location/geo-poi.md)
   + [iBeacon トラッキング](location/ibeacon.md)
+ Target {#target-ios}
   + [Targetの概要](target-main/target-main.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [iOS でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-ios.md)
   + [iOS の Target プレビュー](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience cloudの概要](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform IDサービスのメソッド](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Managerのメソッド](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [tvOSを使用したApple TV実装](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [TVML／TVJS 対応の Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS メソッド](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS拡張の実装](ios-ext/ios-ext.md)
   + [Stand-alone extension implementation](ios-ext/c-stand-alone-extension-implementation.md)
+ [WatchOS 2を使用したApple watchの実装](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK reference](reference/reference.md)
   + [アプリ ID](reference/app-ids.md)
   + [アプリとモバイルWeb間の訪問者の追跡](reference/hybrid-app.md)
   + [iOS device versions](reference/device-versions.md)
+ プライバシーと一般データ保護規則{#privacy-gdpr-ios}
   + [プライバシーと一般データ保護規則](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [保存された識別子の取得](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap プラグイン {#phonegap-ios}
   + [PhoneGapプラグイン](phonegap/phonegap.md)
   + [PhoneGapプラグインのメソッド](phonegap/phonegap-methods.md)
