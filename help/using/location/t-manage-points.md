---
description: 目標地点を作成および管理できます。目標地点では、地理的な場所を定義して、相関関係を分析したり、アプリ内メッセージを使用してターゲット設定したりするのに使用できます。ヒットが目標地点内で送信されると、その目標地点がヒットに追加されます。
keywords: モバイル
seo-description: 目標地点を作成および管理できます。目標地点では、地理的な場所を定義して、相関関係を分析したり、アプリ内メッセージを使用してターゲット設定したりするのに使用できます。ヒットが目標地点内で送信されると、その目標地点がヒットに追加されます。
seo-title: 目標地点の設定
solution: Marketing Cloud、Analytics
title: 目標地点の設定
topic: 指標
uuid: 7b362534-54fb-43a3- b6b2- dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

POIを作成および管理できます。これにより、相関関係のために使用できる地理的な場所、アプリ内メッセージを使用してターゲットを定めることができます。ヒットがPOIで送信されると、POIがヒットに添付されます。

場所を使用する前に、以下の要件を確認してください。

* Analytics モバイルアプリまたは Analytics Premium のご契約が必要です。
* アプリの&#x200B;**[!UICONTROL ロケーションレポート]を有効にする必要があります。**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. 目標地点の管理ページの **[!UICONTROL 「保存」]**&#x200B;をクリックすると、変更内容が目標地点 **** リストにパッケージ化され、ライブアプリの設定ファイルが更新されます。また、アプリケーションでは、更新されたSDKとリモートPOI URLを使用した設定を使用する限り、ユーザーデバイス上でアプリのポイントのリストも更新されます。

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

場所を使用するには、次のタスクを実行します。

1. 目的のアプリの名前をクリックして、そのアプリのアプリ設定ページに移動します。
1. **[!UICONTROL ロケーション]** /目標地点 **[!UICONTROL を管理をクリック]**&#x200B;します。

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

      含める&#x200B;**[!UICONTROL 目標地点]の周囲の半径（メートル単位）を入力します。**&#x200B;例えば、コロラド州デンバー用のPOIを作成する場合、デンバーの都市と周辺の領域を含めるのに十分な半径を指定できますが、コロラドスプリングスは除外できます。

   * **[!UICONTROL マップアイコン]**

      [概要レポート](/help/using/location/c-location-overview.md) と [マップ](/help/using/location/c-map-points.md) レポートに表示するアイコンを選択します。

1. 必要に応じて、追加のPOIを追加します。

   5,000個以下のPOIを追加することをお勧めします。5,000 個を超える目標地点を追加した場合、保存することはできますが、目標地点は 5,000 個未満にすることがベストプラクティスであると知らせる警告メッセージを受け取ることになります。

1. 「**[!UICONTROL 保存]**」をクリックします。

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
