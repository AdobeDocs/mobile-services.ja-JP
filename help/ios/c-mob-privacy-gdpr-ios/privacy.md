---
description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-title: ユーザーのオプトステータスの設定
solution: Marketing Cloud、Analytics
title: ユーザーのオプトステータスの設定
topic: 開発者と導入
uuid: 44a09a25-93c6-4e1a- b69e-710018e8b6c3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

以下の設定を使用して、Analytics、Target および Audience Manager のアクティビティをデバイス上で許可するかどうかを制御できます。

* `privacyDefault` （ [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)）

   この設定は、コード内で変更されるまで保持される初期設定を制御します。

* `setPrivacyStatus`メソッド。

   このメソッドを使用してプライバシー設定を変更した後は、同じメソッドを使用して再度変更されるまで、またはアプリをアンインストールして再度インストールするときまで、変更が保持されます。

   メソッドについて詳しくは、 [設定メソッド](/help/ios/configuration/json-config/json-config.md).

以下に、プライバシーステータスに関する情報を示します。

* **オプトイン**

   * Analytics：ヒットが送信されます。
   * Target：mbox リクエストが送信されます。
   * Audience Manager：シグナルと ID 同期が送信されます。
   * Value in the JSON config file: `optedin`
   * 値 `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **オプトアウト**

   * Analytics：ヒットが破棄されます。
   * Target：mbox リクエストが許可されません。
   * Audience Manager：シグナルと ID 同期が許可されません。
   * Value in the JSON config file: `optedout`
   * 値 `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **不明**

   * Analytics：オフライン追跡が&#x200B;**有効である**&#x200B;場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      オフライン追跡が&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * Target：mbox リクエストが送信されます。
   * Audience Manager：シグナルと ID 同期が送信されます。
   * Value in the JSON config file: `optunknown`
   * 値 `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## 例 {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

