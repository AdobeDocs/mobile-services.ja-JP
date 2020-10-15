---
description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-title: ユーザーのオプトステータスの設定
solution: Experience Cloud,Analytics
title: ユーザーのオプトステータスの設定
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '266'
ht-degree: 100%

---


# ユーザーのオプトステータスの設定 {#setting-the-user-s-opt-status}

この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。

>[!IMPORTANT]
>
>Android SDK 4.15 以降では、プライバシーステータスを `unknown` に設定すると、Audience Manager および Experience Cloud ID のヒットが保持されます。

次の設定を使用することで、Analytics、Target および Audience Manager のアクティビティがデバイスで許可されるかどうかを制御できます。

* 「[ADBMobile JSON 設定](/help/android/configuration/json-config/json-config.md)」の `privacyDefault`。

   この設定では初期設定を制御します。初期設定は、コード内で変更されるまで保持されます。

* `Config.setPrivacyStatus` メソッド。

   この方法を使用してプライバシー設定を変更すると、再び変更するか、アプリをアンインストールして再びインストールするまで、変更は有効となります。メソッドについて詳しくは、「[設定メソッド](/help/android/configuration/methods.md)」を参照してください。

次の表に、各プライバシーステータスを示します。

* **オプトイン**

   * **Analytics**：ヒットが送信されます。
   * **Target**：mbox リクエストが送信されます。
   * **Audience Manager**：シグナルと ID 同期が送信されます。
   * JSON 設定ファイルの値：`optedin`
   * `setPrivacyStatus` の値：`MOBILE_PRIVACY_STATUS_OPT_IN`

* **オプトアウト**

   * **Analytics**：ヒットが破棄されます。
   * **Target**：mbox リクエストは許可されません。
   * **Audience Manager**：シグナルと ID 同期は許可されません。
   * JSON 設定ファイルの値：`optedout`
   * `setPrivacyStatus` の値：`MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Unknown**

   * **Analytics**：オフライン追跡が&#x200B;**有効**&#x200B;である場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変更されるまで、ヒットは保存されます。

      オフライン追跡が<b>有効になっていない</b>場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   * **Target**：mbox リクエストが送信されます。
   * **Audience Manager**：シグナルと ID 同期が送信されます。
   * JSON 設定ファイルの値：`optunknown`
   * `setPrivacyStatus` の値：`MOBILE_PRIVACY_STATUS_UNKNOWN`

## 例 {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

