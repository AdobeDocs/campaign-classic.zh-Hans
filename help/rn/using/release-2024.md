---
product: campaign
title: Campaign Classic 2024 版
description: 详细了解 Campaign Classic 2024 版
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# 2024 版{#release-2024}

## 7.4.1 版 - 内部版本 9383 {#release-7-4-1}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2024 年 6 月 18 日_

### 更改和改进 {#release-7-4-1-changes}

* 由于 Adobe 弃用了服务帐户 (JWT) 凭据，Campaign 与 Adobe 解决方案和应用程序的出站集成现在依赖 OAuth 服务器到服务器凭据。如果已实施出站集成，比如 Campaign-Analytics 集成或 Experience Cloud Triggers 集成，则必须在 2025 年 1 月 27 日前将 Campaign 环境升级到 v7.4.1，并将您的技术帐户迁移到 oAuth。[了解详情](../../integrations/using/oauth-technical-account.md)

* [将 Campaign 技术操作员迁移到 Developer Console](../../technotes/using/ims-migration.md) 并[过渡到用于进行最终用户身份验证的 IMS](../../technotes/using/migrate-users-to-ims.md) 后，您现在可以启用用户界面和 API 限制，以移除特定于原生身份验证的选项和功能。[了解详情](../../technotes/using/impact-ims-migration.md)


### 兼容性更新 {#release-7-4-1-compat}

更新了 [Adobe Campaign 兼容性矩阵](compatibility-matrix.md)，以反映这一新版本中的变化，如下所列。

* Adobe Campaign 现在兼容 **Microsoft Server 2022** 操作系统。
* Adobe Campaign 现在兼容 **RHEL 9** 操作系统。

  >[!CAUTION]
  >
  >作为使用 RHEL 9 的内部部署客户，如果要使用 DKIM（域密钥识别邮件）身份验证，则必须更新系统设置，详情请参阅[本部分](../../installation/using/installing-packages-with-linux.md#rhel-9-update)。


* Adobe Campaign 现在兼容 **Microsoft SQL Server 2022** 和 **Oracle23c**（用作关系数据库管理系统），并兼容联合数据访问 (FDA)。

* Adobe Campaign 现在要求至少安装 Java Development Kit (JDK) 11。在 Windows 上，必须安装有 JRE，如[本节](../../installation/using/application-server.md#jdk)中所述。

* 现已弃用适用于移动应用程序的 Campaign (Neolane) SDK。现在必须过渡到 Adobe Experience Platform SDK。[了解详情](deprecated-features.md)。

  同时，为确保服务连续性，Campaign v7.4 提供：

   * 适用于 iOS 的新 Campaign SDK 1.0.27（兼容 iOS 16 和17），以及最新版本 [Apple iOS 隐私请求要求](https://developer.apple.com/news/?id=r1henawx){target="_blank"}。
   * 适用于 Android 14 的新 Campaign SDK。

### 其他变更 {#release-7-4-1-other}

从 v7.4.1 开始，Campaign 中不再包含 RPM Linux 包的 XML 库。作为内部部署或混合部署客户，您的管理员必须安装这些库。[了解详情](../../installation/using/installing-packages-with-linux.md)

### 修补程序 {#release-7-4-1-patches}

此版本附带以下修复：

NEO-74754、NEO-73174、NEO-72504、NEO-71534、NEO-71473、NEO-70195、NEO-69663、NEO-69651、NEO-67620、NEO-67235、NEO-66797、NEO-64680、NEO-63706、NEO-63657、NEO-62964、NEO-62575、NEO-58734、NEO-40531、NEO-36189、NEO-29592


