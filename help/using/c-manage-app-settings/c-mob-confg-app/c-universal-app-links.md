---
description: ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOSアプリまたはAndroidアプリのディープリンクに接続できます。
keywords: モバイル
seo-description: ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOSアプリまたはAndroidアプリのディープリンクに接続できます。
seo-title: AppleユニバーサルリンクとAndroidアプリリンク
solution: Marketing Cloud、Analytics
title: AppleユニバーサルリンクとAndroidアプリリンク
topic: 指標
uuid: 8d6441dc-4307-4454-95ea- d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# AppleユニバーサルリンクとAndroidアプリリンク{#universal-links-and-app-links}

ユニバーサルリンク（iOS）およびアプリリンク（Android）を使用すると、iOSアプリまたはAndroidアプリのディープリンクに接続できます。

>[!IMPORTANT]
>
>iOS9.2以降、ディープリンクはサポートされていません。アプリまたはWebサイトへのディープリンクにはApple Universal Linkを使用する必要があります。

## ユニバーサルリンク {#section_F8147944679A42E59CF4FD8814E5EF12}

ユニバーサルリンクを使用すると、iOSアプリのディープリンクに接続し、iOS9.2以降でサポートされます。ユニバーサルリンクにアクセスすると、iOSはアプリのディープリンクに直接リンクをリダイレクトします。アプリケーションがインストールされていない場合は、ブラウザーでWebサイトのURLが開きます。ユニバーサルリンクについて詳しくは、「ユニバーサルリンク [のサポート](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)」を参照してください。

## アプリリンク

アプリリンクを使用すると、Androidアプリのディープリンクに接続し、Android6.0以降でサポートされます。アプリリンクにアクセスすると、Androidはアプリのディープリンクに直接リンクをリダイレクトします。アプリケーションがインストールされていない場合は、ブラウザーでWebサイトのURLが開きます。For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## ユニバーサルまたはアプリリンクを使用したマーケティングリンクの作成 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

ユニバーサルまたはアプリリンクを使用するマーケティングリンクを作成できます。

### ユニバーサルリンクの設定

1. iOSアプリでユニバーサルリンクを設定するには、Appleのユニバーサルリンク [の処理に移動](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)してください。

2. Adobe Mobile Servicesで、サイト関連ドキュメントを設定します。

   a. Mobile Servicesホームページで、ユニバーサルリンクを設定するアプリを選択します。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. ユニバーサルリンクを処理するiOSアプリが「アプリストアのアプリ **[!UICONTROL を追加」]** セクションに追加されていることを確認します。

   >[!TIP]
   >
   >「アプリストアのアプリ **[!UICONTROL を追加」]** セクションが表示されない場合は、"App Storeアプリ **[!UICONTROL を追加」]** リンクをクリックします。

   d. **[!UICONTROL 「ユニバーサルリンクとアプリリンクオプション]** 」セクションでiOSアプリを選択し、アプリIDを入力します。

   f. 「 **[!UICONTROL 保存]**」をクリックします。

   少なくとも1つのiOSアプリ選択と1つのApp IDを指定する必要があります。または、エラーが発生します。

   >[!IMPORTANT]
   >
   >「ユニバーサルリンクとアプリリンクのオプション」セクションの「更新」をクリックするとドキュメントを更新できます。**[!UICONTROL ただし、「更新」]**&#x200B;をクリックすると、過去に作成したすべてのユニバーサルリンクまたはアプリリンクが影響を受けることが通知されます。

### ユニバーサルリンクの使用

1. Adobe Mobile Servicesで、ユニバーサルリンクを使用するマーケティングリンクを作成します。

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 「新規 **[!UICONTROL 作成」をクリック]**&#x200B;します。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. 上記のAdobe Mobile *Services* セクションのサイト関連ドキュメントの設定でサイト関連ドキュメントを設定した場合、このオプションはデフォルトで選択されます。

   ドキュメントを設定しなかった場合、「ユニバーサルリンク **[!UICONTROL を使用」オプションまたは「アプリリンクを使用」]** オプションが無効になり、「インタースティシャル **** を使用」がデフォルトで選択されます。

   e. 「ユニバーサルリンク **[!UICONTROL またはアプリリンクを使用」]** オプションが選択されている場合は **[!UICONTROL 、「カスタムパス]** 」フィールドが表示されます。

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「`my/universal/link?os=9.2`の場合、完全なマーケティングリンクURLが表示 `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`されます。

   f. **[!UICONTROL 「決定」]** タブをクリックし、デシジョンツリーを設定します。

   h. iOSアプリがインストールされている場合、アプリケーションはディープリンクをそのロジックで処理します。最終的な宛先は、アプリケーションがインストールされていないときにフォールバックとしてのみ使用されます。アプリケーションがインストールされていないので、最終的な宛先はWebリンクまたはアプリケーションストアのみにできます。

   i. 「 **[!UICONTROL 保存]**」をクリックします。

>[!TIP]
>
>マーケティングリンクが保存されると、マーケティングリンクオプションは変更できません。これは、既に配布されているマーケティングリンクの動作を変更したくないからです。


### アプリリンクの設定

1. Androidアプリでアプリリンクを設定するには、"Androidアプリリンク [を追加」に移動](https://developer.android.com/studio/write/app-link-indexing)します。

1. Adobe Mobile Servicesで、サイト関連ドキュメントを設定します。

   a. Mobile Servicesホームページで、アプリリンクを設定するアプリを選択します。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. ユニバーサルリンクまたはアプリリンクを処理するAndroidアプリが「アプリストアアプリ **[!UICONTROL を追加」]** セクションに追加されていることを確認します。

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. 「 **[!UICONTROL ユニバーサルリンク」および「アプリリンクオプション]** 」セクションまでスクロールします。

   e. **[!UICONTROL 「アプリリンク（Android）]** 」タブをクリックします。

   f. Androidアプリを選択し、SHA-256証明書フィンガープリントを入力します。

   g. 「 **[!UICONTROL 保存]**」をクリックします。

   少なくとも1つのAndroidアプリ選択と1つのSHA-256証明書を提供する必要があります。または、エラーが発生します。

   >[!IMPORTANT]
   >
   >「**[!UICONTROL ユニバーサルリンクとアプリリンクのオプション]」セクションの「****更新[!UICONTROL 」をクリックするとドキュメントを更新できます。]****[!UICONTROL ただし、「更新」]**&#x200B;をクリックすると、過去に作成したすべてのユニバーサルリンクまたはアプリリンクが影響を受けることが通知されます。

### アプリリンクの使用

1. Adobe Mobile Servicesで、アプリリンクを使用するマーケティングリンクを作成します。

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. 「新規 **[!UICONTROL 作成」をクリック]**&#x200B;します。

   c. **[!UICONTROL 「マーケティングリンクオプション]** 」セクションで、「ユニバーサルリンクまたはアプリリンク **[!UICONTROL を使用」を選択]**&#x200B;します。

   d. 手順2からサイト関連ドキュメントを設定した場合、このオプションはデフォルトで選択されます。

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. **[!UICONTROL 「ユニバーサルリンクまたはアプリリンク]** を使用」が選択されている場合は、 **[!UICONTROL 「カスタムパス]** 」フィールドが表示されます。

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「`my/app/link?os=6.0`の場合、完全なマーケティングリンクURLが表示 `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`されます。

   f. **[!UICONTROL 「決定」]** タブをクリックし、デシジョンツリーを設定します。

   g. Androidアプリがインストールされている場合、アプリケーションはディープリンクをそのロジックで処理します。

   最終的な宛先は、アプリケーションがインストールされていない場合のフォールバックケースとしてのみ使用されます。アプリケーションがインストールされていないので、最終的な宛先はWebリンクまたはアプリケーションストアのみにできます。

   h.  「 **[!UICONTROL 保存]**」をクリックします。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. これは、既に配布されているマーケティングリンクの動作を変更したくないからです。

## マーケティングリンクの使用

アプリのメッセージや他の領域でこれらのマーケティングリンクを使用できるようになりました。

>[!IMPORTANT]
>
>ユニバーサルリンクまたはアプリリンクでクリック追跡数を表示したり、インタースティシャルを使用したりすることもできません。

