---
description: 新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページで Analytics SDK の設定をおこなうことができます。
keywords: モバイル
solution: Experience Cloud Services,Analytics
title: SDK Analytics オプションの設定
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 100%

---

# SDK Analytics オプションの設定 {#configure-sdk-analytics-options}

{#eol}

新しいアプリの作成中または既存のアプリの編集中に、アプリ設定ページで Analytics SDK の設定をおこなうことができます。

「**[!UICONTROL Analytics SDK の設定]**」の次のフィールドに情報を入力します。

* **[!UICONTROL HTTPS を使用]**

   HTTPS を有効にしてセキュリティを高めます。

* **[!UICONTROL セッションのヒットの日付を遡る]**

   Adobe SDK がセッション情報のヒットの日付を遡る機能を有効または無効にします。現在、セッション情報のヒットはクラッシュ回数とセッションの長さで構成されています。有効にした場合、Adobe SDK は、セッション情報のヒット日時を、前回のセッションの最後のヒットから 1 秒後に遡って設定します。これによって、クラッシュとセッションのデータを、それらが発生した正しい日付に関連付けます。アプリケーションを新しく起動するたびに、1 つのヒットの日付を遡ります。このオプションを無効にすると、Adobe SDK はセッション情報を現在のライクサイクルに添付します。

* **[!UICONTROL プライバシー]**

   プライバシーオプションを選択します。

   * **[!UICONTROL オプトアウトしたらデータ送信を停止]**
   * **[!UICONTROL オプトイン前は計測するが送信しない]**

* **[!UICONTROL セッションタイムアウト（秒）]**

   セッションタイムアウト値を指定します。

   デフォルト値は 300 秒です。アプリケーションが起動されてから、新しいセッションであると見なされるまでに経過する必要がある時間を秒数で指定します。このタイムアウトは、アプリケーションがバックグラウンドに移行し、再びアクティブになる場合にも適用されます。アプリケーションがバックグラウンドになっている時間はセッションの長さには含まれません。

* **[!UICONTROL バッチ上限]**

   キューに格納してからデータ送信するヒット数を指定します。

   ヒットを直ちに送信するには 0 に設定します。バッチ上限は、連続した呼び出しで送信されるヒット数のしきい値を表します。例えば、このオプションを 10 に設定した場合は、ヒットが 10 個たまるまでヒットをキューに格納します。10 番目のヒットを受信すると、10 個のヒットすべてが連続して送信されます。

* **[!UICONTROL さらに詳細を表示]**

   「**[!UICONTROL さらに詳細を表示]**」リンクをクリックすると、レポートスイート ID とトラッキングサーバー、オフライン追跡の有効／無効、使用されている文字エンコーディングモデル（UTF-8 など）が表示されます。

   オフライントラッキングが有効になっている場合、オフライン時にデバイスによって生成されたデータにはタイムスタンプが付けられ、後で送信されます。このオプションが無効になっている場合、オフラインデータは破棄されます。
