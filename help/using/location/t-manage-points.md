---
description: 目標地点を作成および管理できます。目標地点では、地理的な場所を定義して、相関関係を分析したり、アプリ内メッセージを使用してターゲット設定したりするのに使用できます。ヒットが目標地点内で送信されると、その目標地点がヒットに追加されます。
keywords: モバイル
seo-description: 目標地点を作成および管理できます。目標地点では、地理的な場所を定義して、相関関係を分析したり、アプリ内メッセージを使用してターゲット設定したりするのに使用できます。ヒットが目標地点内で送信されると、その目標地点がヒットに追加されます。
seo-title: 目標地点の設定
solution: Marketing Cloud,Analytics
title: 目標地点の設定
topic: 指標
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

You can create and manage POIs, which allow you to define geographical locations that you can use for correlation purposes, target with in-app messages, and so on. POIでヒットが送信されると、そのPOIがヒットに関連付けられます。

「場所」を使用する前に、次の要件を確認します。

* Analytics モバイルアプリまたは Analytics Premium のご契約が必要です。
* アプリの&#x200B;**[!UICONTROL ロケーションレポート]を有効にする必要があります。**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. 目標地点の管理ページで、「保存」をクリックすると ******** 、変更が目標地点リストにパッケージ化され、ライブアプリの設定ファイルが更新されます。 また、アプリが更新されたSDKとリモートPOI URLの設定を使用する限り、保存すると、ユーザーデバイス上のアプリ内のポイントのリストも更新されます。

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

場所を使用するには、次のタスクを実行します。

1. 目的のアプリの名前をクリックして、そのアプリのアプリ設定ページに移動します。
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![手順の結果](assets/poi.png)

1. 次の各フィールドに情報を入力します。

   * **[!UICONTROL 地点名]**

      **[!UICONTROL 目標地点]の名前を入力します。**

      都市、国、地域の名前を設定できます。競技場や企業など、特定の場所の近くに&#x200B;**[!UICONTROL 目標地点]を作成することもできます。**

   * **[!UICONTROL 緯度]**

      Type the latitude of the **[!UICONTROL Point of Location]**. この情報は、インターネットなど他のソースから取得できます。

   * **[!UICONTROL 経度]**

      Type the longitude of the **[!UICONTROL Point of Location]**. この情報は、インターネットなど他のソースから取得できます。

   * **[!UICONTROL 半径（m）]**

      含める&#x200B;**[!UICONTROL 目標地点]の周囲の半径（メートル単位）を入力します。** For example, if you create a POI for Denver, Colorado, you can specify a radius large enough to include the city of Denver and the surrounding areas, but exclude Colorado Springs.

   * **[!UICONTROL マップアイコン]**

      概要レポートとマップレポートに表示する [アイコン](/help/using/location/c-location-overview.md) を [選択します](/help/using/location/c-map-points.md) 。

1. 必要に応じて、POIを追加します。

   追加するPOIは5,000件以下にすることをお勧めします。 5,000 個を超える目標地点を追加した場合、保存することはできますが、目標地点は 5,000 個未満にすることがベストプラクティスであると知らせる警告メッセージを受け取ることになります。

1. 「**[!UICONTROL 保存]**」をクリックします。

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
