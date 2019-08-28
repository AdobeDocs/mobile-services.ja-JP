---
description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-description: この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。
seo-title: ユーザーのオプトステータスの設定
solution: Marketing Cloud、Analytics
title: ユーザーのオプトステータスの設定
topic: 開発者と導入
uuid: f8a3e6be-44dd-494e-9cda- dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

この情報は、GDPR のデータ削除要求に対処する場合に役立ちます。

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

次の設定を使用することで、Analytics、Target および Audience Manager のアクティビティがデバイスで許可されるかどうかを制御できます。

* `privacyDefault` （ [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md)）

   この設定では初期設定を制御します。初期設定は、コード内で変更されるまで保持されます。

* `Config.setPrivacyStatus` メソッドです。

   このメソッドを使用しておこなったプライバシー設定の変更は、もう一度プライバシー設定を変更するか、アプリをアンインストールしてインストールし直すまで有効なままです。メソッドについて詳しくは、 [設定メソッド](/help/android/configuration/methods.md).

次の表に、各プライバシーステータスを示します。

* **オプトイン**

   * **Analytics**：ヒットが送信されます。
   * **Target**：mbox リクエストが送信されます。
   * **Audience Manager**：シグナルと ID 同期が送信されます。
   * Value in the JSON Config file: `optedin`
   * 値 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **オプトアウト**

   * **Analytics**：ヒットが破棄されます。
   * **Target**：mbox リクエストが許可されません。
   * **Audience Manager**：シグナルと ID 同期が許可されません。
   * Value in the JSON config file: `optedout`
   * 値 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **不明**

   * **Analytics**:オフライン追跡 **が有効**&#x200B;になっている場合、プライバシーステータスがオプトイン（ヒットが送信される）またはオプトアウト（ヒットが破棄される）に変わるまで、ヒットは保存されます。

      オフライン追跡が<b>有効になっていない</b>場合、プライバシーステータスがオプトインに変更されるまで、ヒットは破棄されます。
   * **Target**：mbox リクエストが送信されます。
   * **Audience Manager**：シグナルと ID 同期が送信されます。
   * Value in the JSON config file: `optunknown`
   * 値 `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

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

