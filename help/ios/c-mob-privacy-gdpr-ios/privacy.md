---
description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
solution: Experience Cloud,Analytics
title: ユーザーのオプトステータスの設定
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# ユーザーのオプトステータスの設定 {#setting-the-user-s-opt-status}

この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。

>[!IMPORTANT]
>
>Experience Cloud iOS SDK 4.15 以降では、プライバシーステータスを `unknown` に設定すると、Audience Manager および Experience Cloud ID のヒットが保持されます。

以下の設定を使用して、Analytics、Target および Audience Manager のアクティビティをデバイス上で許可するかどうかを制御できます。

* 「[ADBMobile JSON 設定](/help/ios/configuration/json-config/json-config.md)」の `privacyDefault`。

   この設定は、コード内で変更されるまで保持される初期設定を制御します。

* `setPrivacyStatus`メソッド。

   この方法を使用してプライバシー設定を変更すると、この方法を使用して再び変更するか、アプリをアンインストールして再びインストールするまで、変更は永続的になります。

   メソッドについて詳しくは、「[設定メソッド](/help/ios/configuration/json-config/json-config.md)」を参照してください。

各プライバシーステータスに関する情報を次に示します。

* **オプトイン**

   * Analytics：ヒットが送信されます。
   * Target：mbox リクエストが送信されます。
   * Audience Manager：シグナルと ID 同期が送信されます。
   * JSON 設定ファイルの値：`optedin`
   * `setPrivacyStatus` の値：`ADBMobilePrivacyStatusOptIn`

* **オプトアウト**

   * Analytics：ヒットが破棄されます。
   * Target：mbox リクエストは許可されません。
   * Audience Manager：シグナルと ID 同期は許可されません。
   * JSON 設定ファイルの値：`optedout`
   * `setPrivacyStatus` の値：`ADBMobilePrivacyStatusOptOut`

* **Unknown**

   * Analytics：オフライン追跡が&#x200B;**有効である**&#x200B;場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      オフライン追跡が&#x200B;**有効になっていない**&#x200B;場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。

   * Target：mbox リクエストが送信されます。
   * Audience Manager：シグナルと ID 同期が送信されます。
   * JSON 設定ファイルの値：`optunknown`
   * `setPrivacyStatus` の値：`ADBMobilePrivacyStatusUnknown`

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
