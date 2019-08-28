---
product: モバイルサービス
audience: end-user
user-guide-title: Mobile Services Androidヘルプ
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Androidヘルプ{#android}

+ [Experience Cloud ソリューション用 Android SDK 4.x](overview.md)
+ [リリースノート](rel-notes.md)
+ はじめに{#getting-started-android}
   + [はじめに](getting-started/getting-started.md)
   + [開始する前に](getting-started/requirements.md)
   + [コアの実装とライフサイクル](getting-started/dev-qs.md)
   + [処理ルールとコンテキストデータ](getting-started/proc-rules.md)
   + [Android 4.x ライブラリへの移行](getting-started/migration-v3.md)
+ 設定{#configuration-android}
   + [設定の概要](configuration/configuration.md)
   + [ADBMobile JSON設定ファイル](configuration/json-config/json-config.md)
   + [ADBMobile JSON configパスの上書き](configuration/json-config/json-config-remote.md)
   + [ヒットのバッチ処理](configuration/hit-batching.md)
   + [設定メソッド](configuration/methods.md)
+ [ライフサイクル指標](metrics.md)
+ Analytics{#analytics-android}
   + [解析の概要](analytics-main/analytics-main.md)
   + [アプリの状態の追跡](analytics-main/states.md)
   + [アプリのアクションの追跡](analytics-main/actions.md)
   + [アプリのクラッシュを追跡](analytics-main/crashes.md)
   + [時間指定アクション](analytics-main/timed-actions.md)
   + [訪問者のライフタイム値](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [製品変数](analytics-main/products/products.md)
      + [マーチャンダイジングeVarおよび製品固有のイベントを含む製品変数](analytics-main/products/products-variable-evars-events.md)
   + [イベントシリアル化](analytics-main/event-serialization.md)
   + [ビデオ分析](analytics-main/video-qs.md)
   + ポストバック{#postbacks}
      + [ポストバックの概要](analytics-main/postbacks/postbacks.md)
      + [ポストバックの例](analytics-main/postbacks/postback-example.md)
      + [PII ポストバック](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analyticsのメソッド](analytics-main/analytics-methods.md)
+ 獲得{#acquisition-android}
   + [獲得の概要](acquisition-main/acquisition-main-android.md)
   + [モバイルアプリの獲得](acquisition-main/acquisition.md)
   + [獲得方法](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [ディープリンクのトラッキング](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [サードパーティの据え置きディープリンクのトラッキング](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [マーケティングリンク獲得のテスト](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3獲得のテスト](acquisition-main/t-testing-version-3-acquisition.md)
   + [従来のダウンロード計測のテスト](acquisition-main/t-testing-acquisition.md)
   + [獲得テストのトラブルシューティング](acquisition-main/troubleshoot-acquisition-testing.md)
+ メッセージ{#messaging-android}
   + [メッセージングの概要](messaging-main/messaging-main-android.md)
   + アプリ内メッセージ{#inapp-messaging}
      + [アプリ内メッセージ](messaging-main/messaging/messaging.md)
      + [アプリ内メッセージのトラブルシューティング](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [プッシュメッセージ](messaging-main/push-messaging/push-messaging.md)
      + [ディープリンクによるプッシュメッセージの実装](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [豊富なプッシュ通知の受信](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [プッシュメッセージのトラブルシューティング](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ ロケーション{#location}
   + [場所の概要](location/location.md)
   + [位置情報と目標地点](location/geo-poi.md)
   + [ビーコン追跡](location/beacon.md)
+ Target{#target-android}
   + [Targetの概要](target-main/target-main.md)
   + [Targetの設定](target-main/target.md)
   + [Target メソッド](target-main/c-target-methods.md)
   + [Android でのオファーコンテンツのプリフェッチ](target-main/c-mob-target-prefetch-android.md)
   + [Android の Target プレビュー](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloudの概要](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud IDの設定](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform IDサービスのメソッド](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud Device Co-op](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Managerの概要](audience-manager/audience-manager.md)
   + [Audience Managerの設定](audience-manager/audiencemgmt.md)
   + [Audience Managerメソッド](audience-manager/c-audience-manager-methods.md)
+ ウェアラブル{#wearables-android}
   + [ウェアラブルの概要](wearables/wearables.md)
   + [Androidウェアラブル:はじめに](wearables/android-wearable.md)
   + [Androidウェアラブル:追加のメモ](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDKリファレンスの概要](/help/android/reference/reference.md)
   + [アプリ ID](/help/android/reference/app-ids.md)
   + [アプリとモバイルWebの間の訪問者トラッキング](/help/android/reference/hybrid-app.md)
   + [Androidウィジェット](/help/android/reference/widgets.md)
+ プライバシーと一般データ保護規則{#gdpr-privacy-android}
   + [プライバシーとGDPRの概要](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [保存済み識別子の取得](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [ユーザーのオプトステータスの設定](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap プラグイン{#phonegap-android}
   + [PhoneGapプラグインの概要](phonegap/phonegap.md)
   + [PhoneGapプラグインのメソッド](phonegap/phonegap-methods.md)
