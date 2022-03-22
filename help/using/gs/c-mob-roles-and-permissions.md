---
description: Adobe Analytics では、管理ツールホームページで役割を管理できます。
title: 役割と権限
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# 役割と権限{#roles-and-permissions}

Adobe Analytics では、管理ツールホームページで役割を管理できます。

## 概要 {#section_91B8192891E14E5285718C8118912500}

次の役割は、Mobile Services UI の権限を管理します。

### Analytics 管理者

Analytics 管理者は、ユーザーグループを管理したり、権限を割り当てたりします（その内の 1 つはモバイルアプリ管理）。The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ja)

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

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Mobile Services と Analytics の機能

プッシュメッセージなどの UI の機能にアクセスするための Analytics 契約が会社にない場合、権限レベルにかかわらず、会社のユーザーにはその機能へのアクセス権がありません。

## 役割と権限 {#section_20AA029D5B8C413C8659777E79B11620}

次に、Mobile Services UI の役割と関連する権限を示します。

### Analytics 管理者 permissions

* すべてのユーザーおよびモバイルアプリ管理権限
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >Mobile Services UI でアプリが削除されても、レポートスイートは Analytics にあります。

* アプリ設定

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### モバイルアプリ管理者 permissions

* All User Permissions
* Create App with existing report suite
* アプリ設定

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=ja)
* [グループにユーザーを追加する](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services ユーザー

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >ユーザーは、Adobe Analytics でアクセス権のあるレポートスイートのみ表示できます。

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* レポートの表示と実行
* マーケティングリンクの表示
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
