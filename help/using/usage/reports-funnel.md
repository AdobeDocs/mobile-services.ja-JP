---
description: ファネルレポートは、顧客がモバイルアプリの操作中にマーケティングキャンペーンを放棄した地点や、定義済みのコンバージョンパスからそれた地点を特定します。また、ファネルレポートを使用して、様々なセグメントのアクションを比較できます。
keywords: モバイル
solution: Experience Cloud Services,Analytics
title: ファネルレポート
topic-fix: Reports,Metrics
uuid: 268b4ab9-2e29-4423-9f79-ad93f5231ede
exl-id: 43f9d0aa-0651-42c6-85ea-307ed253cf8d
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 100%

---

# ファネルレポート{#funnel}

{#eol}

**[!UICONTROL ファネル]**&#x200B;レポートは、顧客がモバイルアプリの操作中にマーケティングキャンペーンを放棄した地点や、定義済みのコンバージョンパスからそれた地点を特定します。また、**[!UICONTROL ファネル]**&#x200B;レポートを使用して、様々なセグメントのアクションを比較できます。

各ステップにおける顧客の意思決定を視覚的に捉えることで、意思決定が停止した場所、たどる傾向のあるパスおよび顧客がアプリを離れたタイミングを把握できます。

**[!UICONTROL ファネル]**&#x200B;レポートを開く場合、カスタムファネルを作成する必要があります。詳しくは、「[レポートのカスタマイズ](/help/using/usage/reports-customize/reports-customize.md)」を参照してください。

>[!TIP]
>
>カスタムファネルを保存するには、設定をおこなってレポートを実行した後、URL を保存します。URL は、共有するか、ドキュメント内に保存できます。

次に、このレポートの例を示します。

![](assets/funnel_create.png)

簡単なファネルの例として、3 つのファネルステップと 2 つのファネル比較を使用した設定を次に示します。デモアプリでは、ユーザーが写真などのアイテムを追加して共有できることを前提としています。

カスタマイズウィンドウには、ユーザーがアプリを起動した、アプリのギャラリーから写真を追加した、ソーシャルメディアやテキストメッセージ、デンシメールでアプリから 1 つ以上の写真を共有したことなどを示すセクションがあります。ファネル比較を使用すると、iOS アプリのユーザーと Android アプリのユーザーで、写真の追加と共有のレベルを比較できます。

レポートを生成するには、「**[!UICONTROL 実行]**」をクリックします。

次に、生成レポートの例を示します。

![](assets/funnel.png)

最初のシリーズは、100%のユーザーがアプリを起動したことを示しています。2 つ目のシリーズは、ギャラリーから写真を追加した Android ユーザーの割合が高いことを示しています。3 つ目のシリーズは、iOS ユーザーのほぼ半数が写真を共有し、Android ユーザーは誰も写真を共有しなかったことを示しています。これは、調査が必要な、アプリに関する問題を示している可能性があります。

追加情報を表示するには、グラフ内の棒グラフにカーソルを合わせます。

このレポートでは、次のオプションを設定できます。

* **[!UICONTROL 期間]**

   **[!UICONTROL カレンダー]**&#x200B;アイコンをクリックしてカスタムの期間を選択するか、またはドロップダウンリストからあらかじめ設定されている期間を選択します。
* **[!UICONTROL カスタマイズ]**

   「**[!UICONTROL 表示方法]**」オプションを変更したり、指標およびフィルターを追加したり、追加のシリーズ（指標）を追加したりして、レポートをカスタマイズします。詳しくは、「[レポートのカスタマイズ](/help/using/usage/reports-customize/reports-customize.md)」を参照してください。
* **[!UICONTROL フィルター]**

   「**[!UICONTROL フィルター]**」をクリックし、様々なレポートにわたるフィルターを作成して、すべてのモバイルレポートにおけるセグメントのパフォーマンスを確認します。共通フィルターを定義すると、パス（画面遷移）レポート以外のすべてのレポートに適用できます。詳しくは、「[共通フィルターの追加](/help/using/usage/reports-customize/t-sticky-filter.md)」を参照してください。
* **[!UICONTROL ダウンロード]**

   「**[!UICONTROL PDF]**」または「**[!UICONTROL CSV]**」をクリックして、ドキュメントをダウンロードするか開いて Mobile Services へのアクセス権を持たないユーザーと共有したり、プレゼンテーションで使用したりします。
