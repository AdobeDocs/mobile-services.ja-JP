---
description: Androidウェアラブルアプリからデータを収集できるAndroid拡張機能の設定に役立つ情報を以下に示します。
seo-description: Androidウェアラブルアプリからデータを収集できるAndroid拡張機能の設定に役立つ情報を以下に示します。
seo-title: Android ウェアラブル：追加の注意事項
solution: Experience Cloud,Analytics
title: Android ウェアラブル：追加の注意事項
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 51%

---


# Android ウェアラブル：追加の注意事項{#android-wearables-additional-notes}

Androidウェアラブルアプリからデータを収集できるAndroid拡張機能の設定に役立つ情報を以下に示します。

* AdobeモバイルAndroid Wearables拡張機能を使用するには、Androidバージョン4.4(KitKat)以降が必要です。
* データの取得元が収容アプリか拡張機能かを示す `A.RunMode` という追加のコンテキスト値が 1 つ追加されています。

   * `RunMode` = `Application`

      ヒットはハンドヘルドアプリから取得されます。

   * `RunMode` = `Extension`

      ヒットはウェアラブルから取得されます。

* SDK はハンドヘルドアプリから `aid`/`vid`/`visitor` `service id`/`privacy` ステータスを自動的に同期するので、ウェアラブルアプリから `setPrivacyStatus`/`setUserIdentifier`/`idSync` を呼び出さないでください。
* [アプリ内メッセージ](/help/android/messaging-main/messaging/messaging.md)、[Target](/help/android/target-main/target.md)、および [Audience Manager](/help/android/audience-manager/audiencemgmt.md) はウェアラブルアプリでは無効化されています。

