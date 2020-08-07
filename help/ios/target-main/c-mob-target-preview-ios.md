---
description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-description: Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。
seo-title: iOS の Target プレビュー
title: iOS の Target プレビュー
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 87%

---


# iOS の Target プレビュー{#target-preview-on-ios}

Target プレビューを使用すれば、Target アクティビティに対してエンドツーエンドの QA を容易に実行でき、お使いのデバイスでこうしたアクティビティをプレビューできます。

Target プレビューの設定と使用方法について詳しくは、[Target モバイルプレビュー](https://docs.adobe.com/content/help/ja-JP/target/using/implement-target/mobile-apps/target-mobile-preview.html)を参照してください。

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
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
