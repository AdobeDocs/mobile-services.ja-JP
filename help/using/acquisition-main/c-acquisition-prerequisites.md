---
description: ダウンロード計測用リンクを使用する前に、次の前提条件を満たします。
keywords: モバイル
solution: Experience Cloud Services,Analytics
title: 獲得の前提条件
topic-fix: Metrics
uuid: a224499a-5a51-4ca5-a37b-06792b774671
exl-id: 31201bec-e823-47b1-8912-2f8d69cea5be
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# 獲得の前提条件 {#acquisition-prerequisites}

{#eol}

ダウンロード計測用リンクを使用する前に、次の前提条件を満たします。

マーケティングリンクをトラッキングするには、次の前提条件を満たしていることを確認します。

1. モバイルアプリレポートスイートがあることを確認します。

   新しいモバイルアプリレポートスイートを作成するか、マーケティングリンクから収集されたデータを収集、トラッキングおよびレポートできる既存のレポートスイートがある必要があります。新しいモバイルアプリレポートスイートの作成について詳しくは、「[新しいアプリの追加](/help/using/manage-apps/t-new-app.md)」を参照してください。

1. SDK のバージョンを確認します。

   最新のマーケティングリンクトラッキング機能には、SDK バージョン 4.9 以降が必要です。

   **サポートされる機能**

   | SDK バージョン | [従来のダウンロード計測ビルダー](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md) | [手動リンク構築](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md) | [マーケティングリンクビルダー](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md) |
   |--- |--- |--- |--- |
   | 4.1 ～ 4.5 | ○ | × | × |
   | 4.6 ～ 4.9 | ○ | ○ | × |
   | 4.9 以降 | ○ | ○ | ○ |

1. SDK からの獲得データ送信オプションの有効化

   リンクのトラッキングとレポートをおこなう前に、トラッキングが SDK 設定で有効にされている必要があります。詳しくは、[獲得の設定](/help/using/acquisition-main/t-enable-acquisition.md)を参照してください。

1. アプリストアのアプリを追加

   Apple App Store または Google Play からアプリを追加する必要があります。詳しくは、[App Store からのアプリの追加](/help/using/manage-apps/c-app-store/t-app-store-app.md)を参照してください。
