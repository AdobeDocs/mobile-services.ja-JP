---
description: Adobe Analytics では、管理ツールホームページで役割を管理できます。
title: 役割と権限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# 役割と権限{#roles-and-permissions}

{#eol}

Adobe Analytics では、管理ツールホームページで役割を管理できます。

## 概要 {#section_91B8192891E14E5285718C8118912500}

次の役割は、Mobile Services UI の権限を管理します。

### Analytics 管理者

Analytics 管理者は、ユーザーグループを管理したり、権限を割り当てたりします（その内の 1 つはモバイルアプリ管理）。Experience Cloud管理者は、Adobe IDをAdobe Analyticsアカウントにリンクします。このアカウントを使用すると、Adobe IDを使用して Mobile Services UI にログインできます。 Experience Cloud管理者の詳細は、 [Experience Cloudユーザーと製品を管理する](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ja) (『Experience Cloud中央インターフェイスコンポーネント』ガイド ) を参照してください。

>[!TIP]
>
>既存の Analytics 管理者は、Analytics 管理者の役割を任意のユーザーに割り当てることができます。

### モバイルアプリ管理者

この役割は、Mobile Services UI の管理者です。

>[!IMPORTANT]
>
>プッシュメッセージなどのいくつかの機能では、Analytics 管理者は、ユーザー管理の&#x200B;**[!UICONTROL セグメントの作成]**&#x200B;チェックボックスを選択する必要があります。

## アクセスの管理 {#section_E6939C2695AA4A0DBF432D50B2670920}

次に、Mobile Services UI でのアクセスオプションに関する追加情報を示します。

### アプリおよびレポートスイート

すべての Mobile Services アプリはレポートスイートに結び付けられます。 ユーザーがレポートスイートにアクセスできない場合、そのレポートスイートに関連付けられているアプリにはアクセスできません。

### Mobile Services と Analytics の機能

プッシュメッセージなどの UI の機能にアクセスするための Analytics 契約が会社にない場合、権限レベルにかかわらず、会社のユーザーにはその機能へのアクセス権がありません。

## 役割と権限 {#section_20AA029D5B8C413C8659777E79B11620}

次に、Mobile Services UI の役割と関連する権限を示します。

### Analytics 管理者 permissions

* すべてのユーザーおよびモバイルアプリ管理権限
* 新しいレポートスイートでのアプリの作成
* Mobile Services からアプリを削除

   >[!IMPORTANT]
   >
   >Mobile Services UI でアプリが削除されても、レポートスイートは Analytics にあります。

* アプリ設定

   * ライフサイクルレポートの有効化
   * ロケーションレポートを有効にする
   * 変数および指標の作成/更新/削除

### モバイルアプリ管理者 権限

* すべてのユーザー権限
* 既存のレポートスイートを使用したアプリの作成
* アプリ設定

   * アプリの Mobile SDK オプションの設定
   * アプリの UI 設定
   * リンクされたApp Storeアプリの設定
   * アプリのユニバーサルリンクオプションの設定
   * プッシュサービス証明書と API キーの設定
   * ポストバックの作成/更新/アクティブ化/非アクティブ化/複製/アーカイブ/削除
   * リンク先の作成/更新/アーカイブ/削除

* マーケティングリンクの作成/更新/アーカイブ
* 従来のダウンロード計測用リンクの作成/読み込み/更新/削除
* 場所（目標地点）設定の作成/読み込み/更新/削除
* プッシュメッセージの作成/更新/送信/スケジュール/キャンセル/複製/アーカイブ/削除
* アプリ内メッセージの作成/更新/アクティブ化/非アクティブ化/複製/アーカイブ/削除

グループとユーザーについて詳しくは、 Adobe Analyticsのドキュメントの次のコンテンツを参照してください。

* [ユーザーグループ設定（レガシー）](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=ja)
* [グループにユーザーを追加する](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services ユーザー

この役割には表示のみの権限があり、Mobile Services UI でフィードバックを提供できます。

* Mobile Services UI に関するフィードバックの提供
* アプリを表示

   >[!IMPORTANT]
   >
   >ユーザーは、Adobe Analytics でアクセス権のあるレポートスイートのみ表示できます。

* アプリ設定を表示

   * アプリの SDK 設定をダウンロード
   * すべての UI および SDK 設定を表示
   * 変数と指標の設定の表示
   * ポストバックを表示
   * リンク先を表示

* レポートの表示と実行
* マーケティングリンクの表示
* 従来のダウンロード計測用リンクの表示と書き出し
* 場所（目標地点）設定の表示と書き出し
* プッシュメッセージの表示
* アプリ内メッセージの表示
