---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: ab38c7fd45513c6f7a8ecf7ef8601f0b5a4b5757
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 87%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.4.1 版 - 内部版本 9383 {#release-7-4-1}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2024 年 6 月 18 日_

### 更改和改进 {#release-7-4-1-changes}

* 由于 Adobe 弃用了服务帐户 (JWT) 凭据，Campaign 与 Adobe 解决方案和应用程序的出站集成现在依赖 OAuth 服务器到服务器凭据。如果已实施出站集成，比如 Campaign-Analytics 集成或 Experience Cloud Triggers 集成，则必须在 2025 年 1 月 27 日前将 Campaign 环境升级到 v7.4.1，并将您的技术帐户迁移到 oAuth。[了解详情](../../integrations/using/oauth-technical-account.md)

* [将 Campaign 技术操作员迁移到 Developer Console](../../technotes/using/ims-migration.md) 并[过渡到用于进行最终用户身份验证的 IMS](../../technotes/using/migrate-users-to-ims.md) 后，您现在可以启用用户界面和 API 限制，以移除特定于原生身份验证的选项和功能。[了解详情](../../technotes/using/impact-ims-migration.md)


### 兼容性更新 {#release-7-4-1-compat}

更新了 [Adobe Campaign 兼容性矩阵](compatibility-matrix.md)，以反映这一新版本中的变化，如下所列。

* Adobe Campaign现在与&#x200B;**Microsoft Server 2022**&#x200B;兼容，用作操作系统。
* Adobe Campaign现在与&#x200B;**RHEL 9**&#x200B;兼容，用作操作系统。

  >[!CAUTION]
  >
  >作为使用RHEL 9的内部部署客户，如果要使用DKIM (Domain Keys Identified Mail)身份验证，必须按照[此部分](../../installation/using/installing-packages-with-linux.md#rhel-9-update)中的详细说明更新系统设置。


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

