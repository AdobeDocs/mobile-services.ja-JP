---
description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-title: iOS の Target プレビュー
title: iOS の Target プレビュー
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# iOS の Target プレビュー{#target-preview-on-ios}

Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>To use Target Preview, you need SDK version 4.14.0 or later.

## Target Previewメソッド

* **setPreviewRestartDeeplink**

   プレビューモードでプレビューの選択項目が適用された場合にトリガーされる、アプリケーションのディープリンクを設定します。

   * このメソッドの構文を次に示します。

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * このメソッドのコードサンプルを次に示します。

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
