---
description: 新しいアプリの作成および主要指標の設定をおこなったり、Adobe Analytics および Adobe Audience Manager の SDK オプションを設定したり、獲得および ID サービスオプションを設定したり、設定ファイル、SDK、開発者およびテスター向けツールをダウンローするための情報です。
keywords: モバイル
seo-description: 新しいアプリの作成および主要指標の設定をおこなったり、Adobe Analytics および Adobe Audience Manager の SDK オプションを設定したり、獲得および ID サービスオプションを設定したり、設定ファイル、SDK、開発者およびテスター向けツールをダウンローするための情報です。
seo-title: 新しいアプリの追加
solution: Marketing Cloud,Analytics
title: 新しいアプリの追加
topic: 指標
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 新しいアプリを追加{#add-a-new-app}

新しいアプリの作成および主要指標の設定をおこなったり、Adobe Analytics および Adobe Audience Manager の SDK オプションを設定したり、獲得および ID サービスオプションを設定したり、設定ファイル、SDK、開発者およびテスター向けツールをダウンローするための情報です。

これらの手順は、新しいアプリを追加したり、Adobe Analytics と Adobe Audience Manager の統合を設定したりするのに役立ちます。

アプリを設定する前に、Adobe Mobile Services ユーザーインターフェイスで追加する必要があります。アプリを作成すると、正しい設定が生成され、この設定をそのアプリ用の Mobile SDK を実装している開発者に提供できます。

1. Adobe Mobile Services にサインインして、次のどちらかの作業を実行します。

   * 「**[!UICONTROL 新規作成]」をクリックして、アプリを作成します。**
   * To add additional apps, click Manage Apps in the left navigation menu and click **[!UICONTROL Add]**.

      サインインについて詳しくは、「サインイン」を参照 [してくださ](/help/using/gs/gs-signin.md)い。

      >[!TIP]
      >
      >既存のアプリを管理するには、左側のナビゲーションメニューで「アプリを管理」をクリックし、変更するアプリをクリックします。 アプリの情報ページで、変更を加えることができます。

1. 次のフィールドに情報を入力します。

   **[!UICONTROL レポートスイート]**

   レポートデータが収集され、格納される Adobe Analytics のレポートスイートを指定します。各アプリは、1 つの Analytics レポートスイートと紐付きます。アプリのデータを複数のレポートスイートに送信している場合は、各レポートスイートに対して新しいアプリを追加します。各アプリは、1 つの Analytics レポートスイートと紐付きます。アプリのデータを複数のレポートスイートに送信している場合は、各レポートスイートに対して新しいアプリを追加します。

   Adobe Mobile で Analytics 管理者権限を付与されている場合は、Adobe Mobile で新しいレポートスイートを作成できます。To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL レポートスイート ID]**

      このIDは、Adobe Analyticsのレポートスイートを一意に識別します。 ID の先頭に会社のプレフィックスが自動的に追加されます。

   * **[!UICONTROL 次の設定をコピー]**

      変数、イベント、処理ルールなどの設定は、このレポートスイートとまったく同じように、新しいレポートスイートに設定されます。 **設定のコピー元**&#x200B;レポートスイートがモバイルアプリのテンプレート、またはオフラインで使用可能な既存レポートスイートを選択した場合にのみ、Mobile Servicesで作成されたレポートスイートはオフライン計測が有効になります（タイムスタンプが付けられます）。x

   * **[!UICONTROL タイムゾーン]**

      すべてのレポート日はこのタイムゾーンに設定されます。 デフォルトでは、ブラウザーで使用されているタイムゾーン（に近いもの）が選択されています。

   * **[!UICONTROL 通貨]**

      売上高は、このタイプの通貨として追跡およびレポートされます。
   >[!TIP]
   >
   >仮想レポートスイート(VRS)を使用するには、仮想レポートスイ [ートを参照してください](/help/using/manage-apps/c-mob-vrs.md)。

   * **[!UICONTROL アイコン]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL 名前]**

      (**Optional**) Type a descriptive name for the app. この名前は、アプリをすばやく見つけるのに役立ち、わかりやすい名前を付けると、アプリの目的と設定をすばやく理解するのに役立ちます。

   * **[!UICONTROL タイプ]**

      ドロップダウンリストからタイプを選択します。左側のナビゲーションメニューに表示される使用可能なレポートは、選択したアプリのタイプによって異なります。

      次に、利用可能なタイプを示します。

      * **[!UICONTROL 標準]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL 公開]**

         アプリが Adobe Digital Publishing Suite を使用して構築されている場合、このオプションを選択できます。

      * **[!UICONTROL ゲーム]**

         このオプションは、「**[!UICONTROL 標準]**」オプションに似ていますが、「**ゲーム]」では、レポートで使用される用語がゲーム用の用語に更新されます。[!UICONTROL ** For example, users is changed to players. ゲームアプリには、ゲーム特有のレポートが自動的に表示されます。
   * **[!UICONTROL 説明]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   アプリが追加されたら、さらにオプションを設定できるアプリの情報ページを確認できます。For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
