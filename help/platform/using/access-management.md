---
product: campaign
title: 权限入门
description: 了解如何授予对Campaign功能的访问权限
badge: label="v7" type="信息性" tooltip="仅适用于Campaign Classicv7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---

# 权限入门{#access-management}



Adobe Campaign允许您定义和管理分配给各种操作员的权限。 下面是一组授权或拒绝的权限和限制：

* 访问特定功能（通过指明权限），
* 访问特定记录，
* 创建、修改和/或删除记录（操作、联系人、营销活动、组等）。

这些权限适用于操作员配置文件或操作员组。

它们由链接到操作员与Adobe Campaign的连接模式的安全参数来完成。 有关中安全区域的更多信息 [此页面](../../installation/using/security-zones.md).

您可以向用户授予两种类型的权限：

* 您可以定义赋予权限的运算符组，然后将运算符与一个或多个组相关联。 这使您能够重用权限并使操作员配置文件更加一致。 它还便于用户档案的管理和维护。 有关组创建和管理的信息，请参见 [本节](access-management-groups.md).

* 您可以将命名权限直接归因于用户，在某些情况下，这会使通过组分配的权限过载。 该等权利呈列于 [此页面](access-management-named-rights.md).

>[!NOTE]
>
>在开始定义权限之前，Adobe建议您先阅读 [安全配置核对清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html).

请参阅以下部分以了解如何授予访问权限和设置权限：

* [创建运算符](access-management-operators.md)

* [定义组](access-management-groups.md)

* [添加已命名权限](access-management-named-rights.md)

* [管理Campaign文件夹访问权限](access-management-folders.md)

* [访问权限矩阵](access-management-named-rights.md#access-rights-matrix)


另请参阅:

* [管理工作流的权限](../../workflow/using/managing-rights.md)
* [管理分布式营销的权限](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [管理交互模块的权限](../../interaction/using/operator-profiles.md)
* [筛选对架构的访问权限](../../configuration/using/filtering-schemas.md)
* [限制PI视图](../../configuration/using/restricting-pii-view.md)
