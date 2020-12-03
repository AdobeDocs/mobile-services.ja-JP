---
description: 'アプリ設定ページで、次のような変更をおこなうことができます。 '
seo-description: 'アプリ設定ページで、次のような変更をおこなうことができます。 '
seo-title: アプリの設定
title: アプリの設定
uuid: c088e12d-73b6-40c4-b8cc-ec3bb3d3aa4a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 34%

---


# アプリの設定 {#configuring-your-app}

アプリ設定ページで、次のような変更をおこなうことができます。

* **アプリの情報**

   この節には、アプリ名、アプリのタイプ、主要指標、ライフサイクル、場所のレポートなどの情報が含まれます。

   * **ライフサイクルレポート**

      >[!TIP]
      >
      >Adobe Analytics でレポートスイートを作成した場合は、ライフサイクルレポートを有効にする必要があります。Adobeモバイルでレポートスイートを作成した場合、このオプションはデフォルトで有効になっています。

      このレポートでは、以下の指標を測定できます。

      * **獲得**

         アプリのダウンロードキャンペーンの参照URLを追跡します。 詳しくは、「[獲得](/help/using/acquisition-main/acquisition-main.md)」を参照してください。

      * **ライフサイクル**

         ライフサイクルが実装された後、モバイルライブラリによって自動的に測定される指標およびディメンションを追跡します。 詳しくは、次の節を参照してください。

         * [iOS SDKのライフサイクル指標](/help/ios/metrics.md)
         * [Androidのライフサイクル指標](/help/android/metrics.md)
         * [Windowsライフサイクル指標](/help/universal-windows/metrics.md)
         * [BlackBerryのライフサイクル指標](/help/blackberry/metrics.md)
      * **アプリのアクション**

         アプリ内のアクションに基づいてレポートとパスを有効にします。

      * **ライフタイム値**

         購入、広告表示、ビデオ完了、ソーシャル共有、写真のアップロードなど、アプリのKPIを使用して、時間の経過と共にユーザーがどのように価値を生むかを把握できます。

      * **時間指定イベント**

         アプリの主要な操作（初回購入までの時間など）の間隔を測定します。


* **ロケーションレポート**

   このオプションを使用すると、緯度と経度を追跡し、特定の目標地点(POI)を識別できます。 Bluetoothビーコン（UUID、Major、MinorおよびProximity）も追跡できます。

* **アプリのSDKと開発者テスターツール**

   >[!IMPORTANT]
   >
   >SDK とツールをダウンロードする前に、SDK Analytics のオプションを設定する必要があります。詳しくは、「[SDK Analytics オプションの設定](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)」を参照してください。

   4.x SDKにアップグレードする準備が整ったら、または新しいアプリを作成する場合は、アプリ設定ページの下部から最新のSDKおよび開発ツールをダウンロードします。

   設定が完了したら、設定ファイルを開発者に送信して、データを正しく収集できるようにします。 まだ SDK およびツールのダウンロード準備ができていない場合は、「アプリ設定」をクリックし、アプリをクリックすることで、アプリの情報ページをいつでも表示できます。
