---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 发行说明
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 19%

---

# 最新版本 {#latest-release}

此页面列出了 **Campaign v7 最新版本**&#x200B;中的新增功能、改进和修复。每个新的内部版本都带有一个以颜色突出显示的状态。在[此页面](rn-overview.md)中了解有关 Campaign Classic v7 内部版本状态的更多信息。

## 7.4.1 版 - 内部版本 9383 {#release-7-4-1}

[!BADGE 正式发布版]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hans#rn-statuses" tooltip="正式发布版"}

_2024年6月18日_

### 更改和改进 {#release-7-4-1-changes}

* 随着Adobe弃用服务帐户(JWT)凭据，Campaign与Adobe解决方案和应用程序的出站集成现在依赖于OAuth服务器到服务器凭据。 如果您已实施出站集成，例如Campaign-Analytics集成或Experience Cloud Triggers集成，则必须在2025年1月27日之前将Campaign环境升级到v7.4.1并将您的技术帐户迁移到oAuth。 [了解更多信息](../../integrations/using/oauth-technical-account.md)

* 一旦您拥有 [已将Campaign技术操作员迁移到开发人员控制台](../../technotes/using/ims-migration.md) 和 [转换为IMS以进行最终用户身份验证](../../technotes/using/migrate-users-to-ims.md)，您现在可以启用用户界面和API限制，以删除特定于本机身份验证的选项和功能。 [了解更多信息](../../technotes/using/impact-ims-migration.md)



### 兼容性更新 {#release-7-4-1-compat}

此 [Adobe Campaign的兼容性矩阵](compatibility-matrix.md) 已更新此新版本中的更改，如下所列。

* Adobe Campaign现在与兼容 **Microsoft Server 2022** 和 **RHEL 9** 作为操作系统。

* Adobe Campaign现在与兼容 **Microsoft SQL Server 2022** 和 **oracle23c** 作为关系数据库管理系统，以及作为联合数据访问(FDA)。

* Adobe Campaign现在至少需要Java开发工具包(JDK) 11。 在Windows上，JRE必须可用，如中所述 [本节](../../installation/using/application-server.md#jdk).

* 现已弃用适用于移动应用程序的Campaign (Neolane) SDK。 您现在必须过渡到Adobe Experience Platform SDK。 [了解详情](deprecated-features.md)。

  同时，为确保服务连续性，Campaign v7.4提供了：

   * 适用于iOS的新Campaign SDK 1.0.27，与iOS 16和17兼容，并且是最新版本 [Apple iOS隐私请求要求](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * 适用于Android 14的新Campaign SDK。


### 修补程序 {#release-7-4-1-patches}

此版本附带以下修复：

NEO-74754、NEO-73174、NEO-72504、NEO-71534、NEO-71473、NEO-70195、NEO-69663、NEO-69651、NEO-67620、NEO-67235、NEO-66797、NEO-64680、NEO-63706、NEO-63657、NEO-62964、NEO-62575、NEO-58734、NEO-40531、NEO-36189、NEO-29592

