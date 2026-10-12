---
title: 将Campaign操作员迁移到Adobe Identity Management System (IMS)
description: 了解如何将Campaign操作员迁移到Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%
---
# 将Campaign操作员迁移到Adobe Identity Management System (IMS) {#migrate-users-to-ims}

作为加强安全和身份验证过程的一部分，Adobe Campaign强烈建议将最终用户身份验证模式从登录/密码本机身份验证迁移到Adobe Identity Management System (IMS)。 所有操作员都应实施[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}以连接到Campaign。

在[此页面](ac-ims.md)中了解有关此迁移的更多信息。

## 更改了哪些内容？ {#move-to-ims-changes}

借助Campaign Classic，所有常规用户均已通过Adobe Campaign Identity Management System (IMS)，使用其Adobe ID连接到Adobe客户端控制台。 但是，用户/密码连接仍然可用。 Campaign v8将不再允许这样做。

此外，作为加强安全和身份验证过程的一部分，Adobe Campaign客户端应用程序现在使用IMS技术帐户令牌直接调用Campaign API。 有关技术操作员的迁移详情，请参阅[此页面](ims-migration.md)中的专篇文章。

此更改已适用于Campaign Classic v7，如果要移动到Campaign v8，此更改将为&#x200B;**必需**。

Adobe将支持您完成此迁移工作。 您可以在下面文章中找到详细的上下文和分步指南。

## 您是否受影响？{#migrate-ims-impacts}

此过程适用于所有尚未使用Adobe ID连接到Campaign的Campaign用户。

如果贵组织中的操作员正在使用其登录/密码（也称为）连接到Campaign客户端控制台。 会受到影响，您应该将这些运算符迁移到Adobe IMS，如下所述。

迁移到[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}是确保环境安全和标准化的安全要求，因为大多数其他Adobe Experience Cloud解决方案和应用程序已在IMS上。

此更改适用于从Campaign Classic v7.4.1（和最新的[IMS迁移兼容版本](ac-ims.md#ims-versions)）开始，并且是&#x200B;**强制性的**，必须将其迁移到Adobe Campaign v8。

>[!IMPORTANT]
>
>**控制面板访问影响**
>
>将用户迁移到IMS后，请注意Adobe Admin Console中的任何产品配置文件在其名称中包含“管理员”一词（如“管理员”、“管理员”、“管理员”、“审批管理员”等） 将自动授予对Campaign控制面板的访问权限。 控制面板是一种自助服务工具，允许对Campaign实例进行重大更改。
>
>请仔细查看您的产品配置文件命名约定，确保只有授权用户才能访问控制面板。 在[控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans){target="_blank"}中了解有关管理控制面板权限的详细信息。


## 如何迁移混合和内部部署环境？ {#ims-migration-procedure-on-prem}

下面列出了此迁移的关键步骤：

1. 将您的环境升级到Campaign v7.4.1（或与[IMS迁移兼容的版本](#ims-versions)）。
1. 升级后，您仍然可以使用这两种方法创建新用户，即作为本机用户或者使用IMS。
1. 您的内部Campaign管理员必须配置Adobe IMS，如[此部分](../../integrations/using/configuring-ims.md)中所述。
1. 然后，将唯一的电子邮件添加到Campaign客户端控制台上的所有本机用户。 此步骤在[此部分](https://experienceleague.adobe.com/zh-hans/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"}中详述（Campaign v8文档）。
1. 在Adobe Admin Console中创建用户和产品配置文件，如[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=zh-Hans){target="_blank"}中所述。
1. 为所有操作员启用&#x200B;**与Adobe ID连接**&#x200B;选项。
1. 如[此页面](../../integrations/using/implementing-ims.md)中所述，为您的连接实施Adobe IMS。

您还可以将技术操作员迁移到Adobe Developer Console，如[此技术说明](ims-migration.md)中所述。

## 常见问题解答 {#ims-migration-faq}

有关迁移的常见问题解答（迁移后创建用户、为本机用户添加电子邮件、通过IMS登录、停机、已使用IMS的组织、查看操作员的身份验证类型），请参阅[Campaign v8技术说明](https://experienceleague.adobe.com/zh-hans/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank}（Campaign v8文档）。

>[!MORELIKETHIS]
>
>* [将技术用户迁移到Adobe Developer控制台](ims-migration.md)
>* [Adobe Campaign Classic v7发行说明](../../rn/using/latest-release.md)
>* [什么是Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}
