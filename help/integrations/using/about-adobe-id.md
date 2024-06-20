---
product: campaign
title: 使用您的Adobe ID连接到Adobe Campaign
description: 详细了解Adobe Campaign中的Adobe IMS实施
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 15%

---

# 关于Adobe ID {#about-adobe-id}

AdobeIdentity Management System (IMS)可帮助管理员创建和管理用户对应用程序和服务的访问。 有关不同类型的AdobeID的详细信息，请参阅 [此页面](https://helpx.adobe.com/cn/enterprise/using/identity.html).

Campaign用户可以使用其Adobe ID连接到Adobe Campaign控制台，而不是 [本地用户/密码身份验证](../../platform/using/access-management-operators.md). 此实施具有以下优势：

* 所有 Experience Cloud 解决方案都可以使用相同的 ID。
* 使用具有不同集成的Adobe Campaign时，将保留连接。
* 密码管理策略比本机登录/密码更安全。
* 使用联合 ID 帐户（外部 ID 提供商）。

>[!IMPORTANT]
>
> 请注意，在Campaign v8中，不允许使用用户/密码（又称本机身份验证）连接。 **Adobe建议从Campaign v7.3.5开始执行此迁移，以便能够顺利迁移到Campaign v8。**
>
>了解如何在中迁移到Adobe IMS [本节](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## 更多资源

| 有用页面 | 其他资源 |
|---|---|
| [配置IMS](../../integrations/using/configuring-ims.md) | [Experience Cloud常见问题解答](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [实施IMS](../../integrations/using/implementing-ims.md) | [访问管理](../../platform/using/access-management.md) |
| [IMS疑难解答](../../integrations/using/ims-troubleshooting.md) | [安装Campaign包](../../installation/using/installing-campaign-standard-packages.md) |
