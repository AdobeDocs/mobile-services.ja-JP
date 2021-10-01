---
description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
title: iOS の Target プレビュー
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# iOS の Target プレビュー{#target-preview-on-ios}

Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。

Target プレビューの設定および使用方法について詳しくは、Adobe Targetドキュメントの [Target モバイルプレビュー ](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) を参照してください。

>[!IMPORTANT]
>
>Target プレビューを使用するには、SDK バージョン 4.14.0 以降である必要があります。

## Target プレビューメソッド

* **setPreviewRestartDeeplink**

   プレビューモードでプレビューの選択が適用されたときにトリガーされるアプリのディープリンクを設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
