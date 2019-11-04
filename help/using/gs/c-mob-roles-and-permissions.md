---
description: Adobe Analytics では、管理ツールホームページで役割を管理できます。
seo-description: Adobe Analytics では、管理ツールホームページで役割を管理できます。
seo-title: 役割と権限
title: 役割と権限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: ht
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# 役割と権限{#roles-and-permissions}

Adobe Analytics では、管理ツールホームページで役割を管理できます。

## 概要 {#section_91B8192891E14E5285718C8118912500}

次の役割は、Mobile Services UI の権限を管理します。

### Analytics 管理者

Analytics 管理者は、ユーザーグループを管理したり、権限を割り当てたりします（その内の 1 つはモバイルアプリ管理）。Experience Cloud 管理者は、Adobe ID を Adobe Analytics アカウントとリンクします。これにより、Adobe ID を使用して Mobile Services UI にログインできます。Experience Cloud 管理者について詳しくは、[管理 - ユーザー管理と FAQ](https://docs.adobe.com/content/help/ja-JP/core-services/interface/manage-users-and-products/admin-getting-started.html) を参照してください。

>[!TIP]
>
>既存の Analytics 管理者は、Analytics 管理者の役割を任意のユーザーに割り当てることができます。

この役割について詳しくは、次のコンテンツを参照してください。

* [ユーザー管理の概要](https://docs.adobe.com/content/help/ja-JP/analytics/admin/user-product-management/user-management/users.html)

* [ユーザーおよびグループ権限の変更](https://docs.adobe.com/content/help/ja-JP/analytics/admin/user-product-management/user-management/permissions-changes.html)

### モバイルアプリ管理者

この役割は、Mobile Services UI の管理者です。

>[!IMPORTANT]
>
>プッシュメッセージなどのいくつかの機能では、Analytics 管理者は、ユーザー管理の&#x200B;**[!UICONTROL セグメントの作成]**&#x200B;チェックボックスを選択する必要があります。

## アクセスの管理 {#section_E6939C2695AA4A0DBF432D50B2670920}

次に、Mobile Services UI でのアクセスオプションに関する追加情報を示します。

### アプリおよびレポートスイート

すべての Mobile Services アプリは、レポートスイートに結び付けられています。ユーザーにレポートスイートへのアクセス権がない場合、そのレポートスイートに関連付けられたアプリにアクセスできません。

### Mobile Services と Analytics の機能

プッシュメッセージなどの UI の機能にアクセスするための Analytics 契約が会社にない場合、権限レベルにかかわらず、会社のユーザーにはその機能へのアクセス権がありません。

## 役割と権限{#section_20AA029D5B8C413C8659777E79B11620}

次に、Mobile Services UI の役割と関連する権限を示します。

### Analytics 管理者

* すべてのユーザーおよびモバイルアプリ管理権限
* 新しいレポートスイートを使用したアプリの作成
* Mobile Services からのアプリの削除

   >[!IMPORTANT]
   >
   >Mobile Services UI でアプリが削除されても、レポートスイートは Analytics にあります。

* アプリ設定

   * ライフサイクルレポートを有効にする
   * ロケーションレポートを有効にする
   * 変数および指標の作成／更新／削除

### モバイルアプリ管理者

* すべてのユーザー権限
* 既存のレポートスイートを使用したアプリの作成
* アプリ設定

   * アプリの Mobile SDK オプションの設定
   * アプリの UI 設定
   * リンクしたアプリストアアプリの設定
   * アプリのユニバーサルリンクオプションの設定
   * プッシュサービス証明書および API キーの設定
   * ポストバックの作成／更新／アクティブ化／非アクティブ化／複製／アーカイブ／削除
   * リンク先の作成／更新／アーカイブ／削除

* マーケティングリンクの作成／更新／アーカイブ
* 従来のダウンロード計測用リンクの作成／読み込み／更新／削除
* 場所（目標地点）設定の作成／読み込み／更新／削除
* プッシュメッセージの作成／更新／送信／スケジュール／キャンセル／複製／アーカイブ／削除
* アプリ内メッセージの作成／更新／アクティブ化／非アクティブ化／複製／アーカイブ／削除

グループおよびユーザーについて詳しくは、次を参照してください。

* [ユーザーグループの設定](https://docs.adobe.com/content/help/ja-JP/analytics/admin/user-product-management/user-groups/groups.html)
* [グループにユーザーを追加する](https://docs.adobe.com/content/help/ja-JP/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services ユーザー

この役割には、表示のみの権限があり、Mobile Services UI でフィードバックを提供できます。

* Mobile Services UI 上でフィードバックを提供
* アプリを表示

   >[!IMPORTANT]
   >
   >ユーザーは、Adobe Analytics でアクセス権のあるレポートスイートのみ表示できます。

* アプリ設定の表示

   * アプリ SDK 設定のダウンロード
   * すべての UI および SDK 設定の表示
   * 変数および指標設定の表示
   * ポストバックの表示
   * リンク先の表示

* レポートの表示と実行
* マーケティングリンクの表示
* 従来のダウンロード計測用リンクの表示および書き出し
* 場所（目標地点）設定の表示および書き出し
* プッシュメッセージの表示
* アプリ内メッセージの表示
