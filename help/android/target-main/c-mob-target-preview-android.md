---
description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-title: Android の Target プレビュー
title: Android の Target プレビュー
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Android の Target プレビュー {#target-preview-on-android}

Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/ja-JP/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Target プレビューを使用するには、SDK バージョン 4.14.0 以降である必要があります。

* **setPreviewRestartDeeplink**

   プレビューモードでプレビューの選択が適用されたときにトリガーされるアプリのディープリンクを設定します。

   * このメソッドの構文を次に示します。

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * このメソッドのコードサンプルを次に示します。

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

