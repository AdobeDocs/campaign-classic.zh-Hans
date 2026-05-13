---
title: 迁移到Adobe Identity Management System (IMS)
description: 了解如何将您的身份验证过程迁移到Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
TQID: https://experienceleague.adobe.com/DKwv-rLrgm0ce9cycT1QMtBgQP-2pnMNhqHlH1xJWvo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 479
ht-degree: 6%

---

# 迁移到Adobe Identity Management System (IMS) {#migrate-to-ims}

作为加强安全和身份验证过程的一部分，Adobe Campaign强烈建议将最终用户身份验证模式从登录/密码本机身份验证迁移到[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}。

此外，Adobe Campaign客户端应用程序现在使用IMS技术帐户令牌直接调用Campaign API。 您必须将技术操作员迁移到Adobe Developer Console。

>[!CAUTION]
>
>此更改已适用于Campaign Classic v7，如果要移动到Campaign v8，此更改将为&#x200B;**必需**。 Campaign v8中不允许进行本机用户/密码身份验证。 **Adobe建议从Campaign v7.3.5开始执行此迁移以便能够顺利迁移到Campaign v8。**
>

## 迁移步骤 {#ims-steps}

迁移到[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}是确保环境安全和标准化的安全要求，因为大多数其他Adobe Experience Cloud解决方案和应用程序已在IMS上。

Adobe将支持您完成此迁移工作。 您可以在以下文章中找到详细的上下文和分步指南：

* 在[此页面](migrate-users-to-ims.md)中详细描述了最终用户身份验证的迁移。
* 在[此页面](ims-migration.md)中详细描述了技术操作员身份验证的迁移。
* 从Campaign v7.4.1开始，启用用户界面和API限制以删除特定于本机身份验证的选项和功能，如[此页面](impact-ims-migration.md)中所述。


## IMS迁移兼容版本 {#ims-versions}

此迁移的先决条件是将您的环境升级到以下产品版本之一：

* Campaign v7.4.1（推荐）
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

[发行说明](../../rn/using/latest-release.md)中详细介绍了这些Campaign版本。

## 常见问题解答 {#ims-migration-faq}

### 我何时可以开始迁移？ {#ims-migration-start}

迁移到[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}的建议是将您的环境升级到Campaign Classic v7.4.1（或[IMS迁移兼容版本](#ims-versions)）。

升级到最新版本后，您可以在暂存环境中启动IMS迁移，并相应地规划生产环境。

### 将内部版本升级到Campaign Classic v7.4.1后会发生什么？ {#ims-migration-after-upgrade}

在环境升级到Campaign Classic v7.4.1（或[IMS迁移兼容版本](#ims-versions)）后，您可以开始过渡到[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}。

### 迁移何时完成？ {#ims-migration-end}

最终用户迁移和技术操作员迁移到Adobe Identity Management System (IMS)后，您必须更新环境以删除特定于本机身份验证且不再适用于IMS身份验证的选项。 此更新仅从Campaign v7.4.1开始可用。 [了解详情](impact-ims-migration.md)



## 有用的链接 {#ims-useful-links}

* [将最终用户迁移到IMS](migrate-users-to-ims.md)
* [将技术操作员迁移到Adobe Developer控制台](ims-migration.md)
* [Adobe Campaign Classic v7最新发行说明](../../rn/using/latest-release.md)
* [Adobe Identity Management System (IMS)是什么](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}
