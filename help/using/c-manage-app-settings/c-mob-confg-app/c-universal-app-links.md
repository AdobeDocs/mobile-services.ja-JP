---
description: ユニバーサルリンク(iOS)およびアプリリンク(Android)を使用すると、iOSまたはAndroidアプリでディープリンクに接続できます。
keywords: モバイル
seo-description: ユニバーサルリンク(iOS)およびアプリリンク(Android)を使用すると、iOSまたはAndroidアプリでディープリンクに接続できます。
seo-title: Apple Universal LinksとAndroid App Links
solution: Marketing Cloud,Analytics
title: Apple Universal LinksとAndroid App Links
topic: 指標
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links and Android App Links{#universal-links-and-app-links}

Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.

>[!IMPORTANT]
>
>Starting with iOS 9.2, deep linking is not supported. You must use Apple Universal Links for deep linking to your app or website.

## ユニバーサルリンク {#section_F8147944679A42E59CF4FD8814E5EF12}

Universal Links allow you to connect to deep links in your iOS app and are supported in iOS 9.2 or later. ユニバーサルリンクにアクセスすると、iOSはアプリ内のディープリンクに直接リダイレクトします。 アプリがインストールされていない場合は、代わりにブラウザーでWebサイトのURLが開かれます。 ユニバーサルリンクについて詳しくは、「ユニバーサルリンクのサ [ポート」を参照してくださ](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)い。

## アプリリンク

「アプリリンク」を使用すると、Androidアプリ内のディープリンクに接続でき、Android 6.0以降でサポートされます。 アプリリンクにアクセスすると、Androidはアプリ内のディープリンクに直接リダイレクトします。 アプリがインストールされていない場合は、代わりにブラウザーでWebサイトのURLが開かれます。 For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## ユニバーサルリンクまたはアプリリンクを使用したマーケティングリンクの作成 {#section_609ADEFFB9B441C4A8C45E936D0DC859}

ユニバーサルリンクまたはアプリリンクを使用するマーケティングリンクを作成できます。

### Configure a Universal Link

1. iOSアプリでユニバーサルリンクを設定するには、「Appleでのユニバーサルリ [ンクの処理」に進みます](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)。

2. Adobe Mobile Servicesで、サイト関連ドキュメントを設定します。

   a.Mobile Servicesホームページで、ユニバーサルリンクを設定するアプリを選択します。

   b. Click **[!UICONTROL Manage App Settings]**.

   c.ユニバーサルリンクを処理するiOSアプリが「App Storeアプリを追加」セクションに追加さ **[!UICONTROL れていることを確認します]** 。

   >[!TIP]
   >
   >If the Add App Store Apps section does not display, click the Add App Store App link.********

   d. In the Universal Links and App Links Options section, select an iOS app and type the App ID.****

   f.Click Save.****

   You must provide at least one iOS app selection and one App ID, or you will receive an error.

   >[!IMPORTANT]
   >
   >「ユニバーサルリンクとアプリリンクのオプション」セクションの「更新」をクリックするとドキュメントを更新できます。However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### ユニバーサルリンクの使用

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b.「新規作 **[!UICONTROL 成」をクリックします]**。

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d.上記の「Adobe Mobile Servicesでのサイト関連ドキュメントの設定」でサ *イト関連ドキュメントを設定した場合* 、このオプションはデフォルトで選択されています。

   ドキュメントを設定しなかった場合、「ユニバーサルリンク **[!UICONTROL またはアプリリンクを使用]** 」オプションが無効になり、「インタースティ **[!UICONTROL シャルを使用]** 」がデフォルトで選択されます。

   e.「ユニバーサル **[!UICONTROL リンクまたはアプリリンクを使用]** 」オプションが選択されている場合は、「カス **[!UICONTROL タムパス]** 」フィールドが表示されます。

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「 に設 `my/universal/link?os=9.2`定されている場合、完全なマーケティングリンクURLが表示され `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`ます。

   f. Click the Decisions tab and configure your decision tree.****

   h.iOSアプリがインストールされている場合、アプリはそのロジックでディープリンクを処理します。 最終的な宛先は、アプリがインストールされていない場合のフォールバックとしてのみ機能します。 アプリがインストールされていないので、最終的なリンク先はWebリンクまたはアプリストアのみにすることができます。

   i.「保存」をク **[!UICONTROL リックしま]**&#x200B;す。

>[!TIP]
>
>マーケティングリンクを保存すると、マーケティングリンクオプションを変更できなくなります。 これは、既に配布されている可能性のあるマーケティングリンクの動作を変更しないためです。


### アプリリンクの設定

1. To set up App Links in your Android app, go to Add Android App Links.[](https://developer.android.com/studio/write/app-link-indexing)

1. Adobe Mobile Servicesで、サイト関連ドキュメントを設定します。

   a.Mobile Servicesホームページで、アプリリンクを設定するアプリを選択します。

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the Android app that handles Universal Links or App Links is added to the Add App Store Apps section.****

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d.「ユニバーサルリンクとア **[!UICONTROL プリリンクのオプション」セクションまでスクロールしま]** す。

   e.「アプリリン **[!UICONTROL ク(Android)」タブをクリックします]** 。

   f.Androidアプリを選択し、SHA-256証明書指紋を入力します。

   g.「保存」をク **[!UICONTROL リックしま]**&#x200B;す。

   少なくとも1つのAndroidアプリと1つのSHA-256証明書を指定する必要があります。指定しないと、エラーが表示されます。

   >[!IMPORTANT]
   >
   >「**[!UICONTROL ユニバーサルリンクとアプリリンクのオプション]」セクションの「****更新[!UICONTROL 」をクリックするとドキュメントを更新できます。]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### アプリリンクの使用

1. Adobe Mobile Servicesで、「アプリリンク」を使用するマーケティングリンクを作成します。

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. In the Marketing Link Options section, select Use Universal Links or App Links.********

   d.手順2でサイト関連ドキュメントを設定した場合、このオプションはデフォルトで選択されています。

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. If Use Universal Links or App Links is selected, the Custom Path field is displayed.********

   このフィールドでは、クエリパラメーターと共に、ドメインに続いて URL パスを定義できます。例えば、「 に設 `my/app/link?os=6.0`定されている場合、完全なマーケティングリンクURLが表示され `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`ます。

   f. Click the Decisions tab and configure your decision tree.****

   g. If the Android app is installed, the app handles the deeplink with its logic.

   The final destination serves only as the fallback case for when the app is not installed. アプリがインストールされていないので、最終的なリンク先はWebリンクまたはアプリストアのみにすることができます。

   h.「保存」をク **[!UICONTROL リックしま]**&#x200B;す。

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. This is because you do not want to change the behavior of the Marketing Links that may have already been distributed.

## マーケティングリンクの使用

これらのマーケティングリンクは、メッセージングやアプリ内の他の領域で使用できるようになりました。

>[!IMPORTANT]
>
>ユニバーサルリンクまたはアプリリンクを使用したクリック追跡カウントは表示されず、インタースティシャルも使用できません。

