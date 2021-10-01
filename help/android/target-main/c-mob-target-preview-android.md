---
description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
title: Android の Target プレビュー
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Android の Target プレビュー {#target-preview-on-android}

Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。

Target プレビューの設定および使用方法について詳しくは、Adobe Targetユーザーガイドの「[Target Mobile Preview](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html)」を参照してください。

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
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
