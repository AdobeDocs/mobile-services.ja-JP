---
description: この情報は、Android ウェアラブルアプリからデータを収集できる Android 拡張機能を設定する場合に役立ちます。
seo-description: この情報は、Android ウェアラブルアプリからデータを収集できる Android 拡張機能を設定する場合に役立ちます。
seo-title: Android Wearables  Additional Notes
solution: Marketing Cloud,Analytics
title: Android Wearablesに関する追加の注意事項
topic: 開発者と導入
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

この情報は、Android ウェアラブルアプリからデータを収集できる Android 拡張機能を設定する場合に役立ちます。

* Adobe Mobile Android ウェアラブル拡張機能を使用するには、Android バージョン 4.4（KitKat）以上が必要です。
* データの取得元が収容アプリか拡張機能かを示す `A.RunMode` という追加のコンテキスト値が 1 つ追加されています。

   * `RunMode` = `Application`

      このヒットはハンドヘルドアプリから得られます。

   * `RunMode` = `Extension`

      ヒットはウェアラブルアプリから発生します。

* SDKは、ハンドヘルドアプリからウェアラブルアプリに `aid`//`vid`/`visitor` /ステータスを自動的に同期するので、ウェアラブルアプリから `service id`/`privacy` / `setPrivacyStatus`/`setUserIdentifier``idSync` を呼び出さないでください。
* [アプリ内メッセージ](/help/android/messaging-main/messaging/messaging.md)、 [Target](/help/android/target-main/target.md)、 [](/help/android/audience-manager/audiencemgmt.md) Audience Managerは、ウェアラブルアプリでは無効です。

