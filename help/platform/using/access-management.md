---
product: campaign
title: 权限入门
description: 了解如何授予对Campaign功能的访问权限
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 6%

---

# 权限入门{#access-management}


>[!CAUTION]
>
>从Campaign Classic v7.3.1开始，所有操作员都应使用[Adobe Identity Management System (IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}连接到Campaign。
>
>作为加强安全和身份验证过程的一部分，Adobe Campaign强烈建议将所有现有的操作员身份验证模式从登录/密码本机身份验证迁移到Adobe Identity Management System (IMS)。 在[此页面](../../technotes/using/migrate-users-to-ims.md)中了解如何迁移操作员。
> 
>进行此迁移后，请注意，以下部分不再适用。  请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hans){target="_blank"}以了解如何使用Adobe IMS设置权限。


Adobe Campaign允许您定义和管理分配给各种操作员的权限。 这些权限是一组授权或拒绝的权限和限制：

* 访问特定功能（通过指明权限），
* 访问特定记录，
* 创建、修改和/或删除记录（操作、联系人、营销活动、组等）。

这些权限适用于操作员配置文件或操作员组。

它们由安全参数完成，这些安全参数链接到操作员与Adobe Campaign的连接模式。 有关[此页面](../../installation/using/security-zones.md)中安全区域的详细信息。

您可以向用户授予两种类型的权限：

* 您可以定义赋予权限的运算符组，然后将运算符与一个或多个组关联。 这使您可以重复使用权限并使操作员配置文件更加一致。 它还便于用户档案的管理和维护。 [此部分](access-management-groups.md)中介绍了组的创建和管理。

* 您可以将命名权限直接归因于用户，在某些情况下，这会使通过组分配的权限过载。 这些权限显示在[此页面](access-management-named-rights.md)中。

>[!NOTE]
>
> * 在开始定义权限之前，Adobe建议您先阅读[安全配置核对清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。
> * 要了解有关权限的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}上的详细说明。

<!--

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->