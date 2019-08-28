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
   + [概要概要](getting-started/getting-started.md)
   + [開始する前に](getting-started/requirements.md)
   + [コアの実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ](getting-started/proc-rules.md)
   + [Swift統合](getting-started/swift-integration.md)
   + [4. x iOSライブラリへの移行](getting-started/migration-v3.md)
+ 設定 {#config-ios}
   + [設定の概要](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [ADBMobile JSON configパスの上書き](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定メソッド](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics {#analytics-ios}
   + [解析の概要](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュを追跡](analytics-main/crashes.md)
   + [時間指定アクション](analytics-main/timed-actions.md)
   + [訪問者のライフタイム値](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [製品変数](analytics-main/products/products.md)
      + [マーチャンダイジングeVarおよび製品固有のイベントを含む製品変数](analytics-main/products/products-variable-evars-events.md)
   + [イベントシリアル化](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック {#postbacks}
      + [ポストバックの概要](analytics-main/postback/postback.md)
      + [ポストバックの例](analytics-main/postback/postback-example.md)
      + [PIIポストバック](analytics-main/postback/c-pii-postbacks.md)
   + [Analyticsのメソッド](analytics-main/analytics-methods.md)
+ 獲得 {#acquisition-ios}
   + [獲得の概要](acquisition-main/acquisition-main.md)
   + [モバイルアプリの獲得](acquisition-main/acquisition.md)
   + [獲得方法](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [ディープリンクのトラッキング](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティの据え置きディープリンクのトラッキング](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [マーケティングリンク獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3獲得のテスト](acquisition-main/t-testing-version-3-acquisition.md)
   + [従来のダウンロード計測のテスト](acquisition-main/t-testing-acquisition.md)
   + [Apple Search Ads](acquisition-main/c-apple-search-ads.md)
+ メッセージ {#messaging-ios}
   + [メッセージングの概要](messaging-main/messaging-main.md)
   + アプリ内メッセージ {#in-app-messaging}
      + [アプリ内メッセージ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [ディープリンクによるプッシュメッセージの実装](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [豊富なプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ ロケーション {#location-ios}
   + [場所の概要](location/location.md)
   + [位置情報と目標地点](location/geo-poi.md)
   + [iBeacon トラッキング](location/ibeacon.md)
+ Target {#target-ios}
   + [Targetの概要](target-main/target-main.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [iOS でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-ios.md)
   + [iOS の Target プレビュー](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloudの概要](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform IDサービスのメソッド](marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Managerメソッド](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [tvOSを使用したApple TV実装](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [TVML／TVJS 対応の Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS メソッド](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS拡張機能の実装](ios-ext/ios-ext.md)
   + [スタンドアロン拡張の実装](ios-ext/c-stand-alone-extension-implementation.md)
+ [WatchOS2によるApple Watchの導入](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDKリファレンス](reference/reference.md)
   + [アプリ ID](reference/app-ids.md)
   + [アプリとモバイルWebの間の訪問者トラッキング](reference/hybrid-app.md)
   + [iOSデバイスのバージョン](reference/device-versions.md)
+ プライバシーと一般データ保護規則{#privacy-gdpr-ios}
   + [プライバシーと一般データ保護規則](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [保存済み識別子の取得](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap プラグイン {#phonegap-ios}
   + [PhoneGapプラグイン](phonegap/phonegap.md)
   + [PhoneGapプラグインのメソッド](phonegap/phonegap-methods.md)
