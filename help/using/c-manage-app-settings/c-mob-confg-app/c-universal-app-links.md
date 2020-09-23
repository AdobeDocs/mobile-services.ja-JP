---
description: ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOS または Android アプリでディープリンクに接続できます。
keywords: mobile
seo-description: ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOS または Android アプリでディープリンクに接続できます。
seo-title: Apple ユニバーサルリンクと Android アプリリンク
solution: Experience Cloud,Analytics
title: Apple ユニバーサルリンクと Android アプリリンク
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 97%

---


# Apple ユニバーサルリンクと Android アプリリンク{#universal-links-and-app-links}

ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOS または Android アプリでディープリンクに接続できます。

>[!IMPORTANT]
>
>iOS 9.2 以降では、ディープリンクはサポートされていません。アプリまたは Web サイトへのディープリンクには、Apple ユニバーサルリンクを使用する必要があります。

## ユニバーサルリンク {#section_F8147944679A42E59CF4FD8814E5EF12}

ユニバーサルリンクを使用すると、iOS アプリ内のディープリンクに接続できます（iOS 9.2 以降でサポートされます）。ユニバーサルリンクにアクセスすると、iOS はリンクをアプリ内のディープリンクに直接リダイレクトします。アプリがインストールされていない場合は、代わりにブラウザーで Web サイトの URL が開きます。ユニバーサルリンクについて詳しくは、「[Support Universal Links（ユニバーサルリンクのサポート）](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)」を参照してください。

## アプリリンク

アプリリンクを使用すると、Android アプリ内のディープリンクに接続できます（Android 6.0 以降でサポートされます）。アプリリンクにアクセスすると、Android はアプリ内のディープリンクに直接リダイレクトします。アプリがインストールされていない場合は、代わりにブラウザーで Web サイトの URL が開きます。アプリリンクについて詳しくは、[Android アプリリンクの処理](https://developer.android.com/training/app-links/index.html)を参照してください。

## ユニバーサルリンクまたはアプリリンクを使用したマーケティングリンクの作成 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

ユニバーサルリンクまたはアプリリンクを使用するマーケティングリンクを作成できます。

### ユニバーサルリンクの設定

1. iOS アプリでユニバーサルリンクを設定するには、「[Apple でのユニバーサルリンクの処理](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)」に進みます。

2. Adobe Mobile Services で関連ドキュメントを設定します。

   Mobile Services ホームページで、ユニバーサルリンクを設定するアプリを選択します。

   b. **[!UICONTROL アプリ設定]** をクリックします。

   c. ユニバーサルリンクを処理する iOS アプリが **[!UICONTROL アプリストアのアプリを追加]** セクションに追加されたことを確認します。

   >[!TIP]
   >
   >**[!UICONTROL アプリストアのアプリを追加]** セクションが表示されない場合は、**[!UICONTROL アプリストアのアプリを追加]** リンクをクリックしす。

   d. **[!UICONTROL ユニバーサルリンクとアプリリンクのオプション]** セクションで、iOS アプリを選択してアプリ ID を入力します。

   f. **[!UICONTROL 保存]** をクリックします。

   iOS アプリを 1 つ以上とアプリ ID を 1 つ提供する必要があります。提供できない場合はエラーが発生します。

   >[!IMPORTANT]
   >
   >「ユニバーサルリンクとアプリリンクのオプション」セクションの「更新」をクリックするとドキュメントを更新できます。ただし、**[!UICONTROL 更新]** をクリックすると、それまでに作成したすべてのユニバーサルリンク／アプリリンクに影響するという警告が表示されます。

### ユニバーサルリンクの使用

1. Adobe Mobile Services で、ユニバーサルリンクを使用するマーケティングリンクを作成します。

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. **[!UICONTROL 新規作成]** をクリックします。

   c. **[!UICONTROL マーケティングリンクオプション]** で、**[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** を選択します。

   d. 「*Adobe Mobile Services でサイト関連のドキュメントを設定する*」セクションでサイト関連ドキュメントを設定した場合、このオプションはデフォルトで選択されます。

   ドキュメントを設定していない場合、**[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** オプションが無効化され、デフォルトで **[!UICONTROL インタースティシャルを使用]** が選択されます。

   e. **[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** オプションが選択されている場合は、**[!UICONTROL カスタムパス]** フィールドが表示されます。

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「`my/universal/link?os=9.2`」と入力すると、完全なマーケティングリンク URL は `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2` になります。

   f. **[!UICONTROL 決定]** タブをクリックし、デシジョンツリーを設定します。

   h. iOS アプリがインストールされている場合、ディープリンクはアプリのロジックで処理されます。最終的な宛先は、アプリがインストールされていない場合のフォールバックとしてのみ機能します。アプリがインストールされていないので、最終的な宛先に指定できるのは Web リンクまたはアプリストアのみです。

   i. **[!UICONTROL 保存]** をクリックします。

>[!TIP]
>
>マーケティングリンクが保存されると、「マーケティングリンクオプション」は変更できなくなります。これは、既に配布されたマーケティングリンクの動作が変化しないようにするためです。


### アプリリンクの設定

1. Android アプリでアプリリンクを設定するには、「[Android アプリリンクの追加](https://developer.android.com/studio/write/app-link-indexing)」に移動します。

1. Adobe Mobile Services で関連ドキュメントを設定します。

   a. Mobile Services ホームページで、アプリリンクを設定するアプリを選択します。

   b. **[!UICONTROL アプリ設定]** をクリックします。

   c. ユニバーサルリンクまたはアプリリンクを処理する Android アプリが **[!UICONTROL アプリストアのアプリを追加]** セクションに追加されたことを確認します。

   >[!TIP]
   >
   >このセクションが表示されない場合、**[!UICONTROL アプリストアのアプリを追加]** リンクをクリックします。

   d.**[!UICONTROL ユニバーサルリンクとアプリリンクのオプション]** セクションまでスクロールします。

   e. **[!UICONTROL アプリリンク（Android）]** タブをクリックします。

   f. Android アプリを選択し、SHA-256 証明書フィンガープリントを入力します。

   g. **[!UICONTROL 保存]** をクリックします。

   Android アプリを 1 つ以上と SHA-256 証明書を提供する必要があります。提供できない場合はエラーが発生します。

   >[!IMPORTANT]
   >
   >**[!UICONTROL ユニバーサルリンクとアプリリンクのオプション]**&#x200B;セクションの&#x200B;**[!UICONTROL 更新]**&#x200B;をクリックするとドキュメントを更新できます。ただし、**[!UICONTROL 更新]** をクリックすると、それまでに作成したすべてのユニバーサルリンク／アプリリンクに影響するという警告が表示されます。

### アプリリンクの使用

1. Adobe Mobile Services で、アプリリンクを使用するマーケティングリンクを作成します。

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. **[!UICONTROL 新規作成]** をクリックします。

   c. **[!UICONTROL マーケティングリンクオプション]** セクションで、**[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** を選択します。

   d. 手順 2 でサイト関連ドキュメントを設定した場合、このオプションはデフォルトで選択されます。

   そうでない場合、**[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** オプションは無効になっていて、デフォルトで **[!UICONTROL インタースティシャルを使用]** が選択されます。

   e. **[!UICONTROL ユニバーサルリンクまたはアプリリンクを使用]** が選択されている場合は、**[!UICONTROL カスタムパス]** フィールドが表示されます。

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「`my/app/link?os=6.0`」と入力すると、完全なマーケティングリンク URL は `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0` になります。

   f. **[!UICONTROL 決定]** タブをクリックし、デシジョンツリーを設定します。

   ｇ. Android アプリがインストールされている場合、ディープリンクはアプリのロジックで処理されます。

   最終的な宛先は、アプリがインストールされていない場合のフォールバックケースとしてのみ機能します。アプリがインストールされていないので、最終的な宛先に指定できるのは Web リンクまたはアプリストアのみです。

   h. **[!UICONTROL 保存]** をクリックします。

>[!TIP]
>
>マーケティングリンクを保存すると、**[!UICONTROL マーケティングリンクオプション]** は変更できなくなります。これは、既に配布されたマーケティングリンクの動作が変化しないようにするためです。

## マーケティングリンクの使用

これらのマーケティングリンクを、メッセージやアプリ内の他の領域で使用できるようになりました。

>[!IMPORTANT]
>
>ユニバーサルリンクまたはアプリリンクを使用したクリックの追跡カウントは表示されず、インタースティシャルも使用できません。

