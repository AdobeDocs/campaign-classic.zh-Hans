---
product: campaign
title: 权限入门
description: 了解如何授予对Campaign功能的访问权限
badge: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---

# 权限入门{#access-management}



Adobe Campaign允许您定义和管理分配给各种运算符的权限。 这些权限和限制是授权或拒绝的一组权限和限制：

* 访问特定功能（通过指定权限），
* 访问某些记录，
* 创建、修改和/或删除记录（操作、联系人、营销活动、组等）。

权限适用于操作员配置文件或操作员组。

这些配置文件由链接到操作员连接模式的安全参数完成，Adobe Campaign。 有关 [本页](../../installation/using/security-zones.md).

您可以向用户授予两种类型的权限：

* 您可以定义属性权限的运算符组，然后将运算符与一个或多个组关联。 这样，您就可以重复使用权限，并使操作员配置文件更加一致。 它还有助于用户档案的管理和维护。 集团创建及管理于 [此部分](access-management-groups.md).

* 您可以将命名权限直接归因于用户，在某些情况下，会导致通过组分配的权限过载。 该等权利于 [本页](access-management-named-rights.md).

>[!NOTE]
>
>在开始定义权限之前，Adobe建议您 [安全配置检查列表](https://helpx.adobe.com/cn/campaign/kb/acc-security.html).

在以下部分中了解如何授予访问权限和设置权限：

* [创建运算符](access-management-operators.md)

* [定义群组](access-management-groups.md)

* [添加命名权限](access-management-named-rights.md)

* [管理Campaign文件夹访问权限](access-management-folders.md)

* [访问权限矩阵](access-management-named-rights.md#access-rights-matrix)


另请参阅:

* [管理工作流的权限](../../workflow/using/managing-rights.md)
* [管理分布式营销的权限](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [管理交互模块的权限](../../interaction/using/operator-profiles.md)
* [筛选对架构的访问](../../configuration/using/filtering-schemas.md)
* [限制PI视图](../../configuration/using/restricting-pii-view.md)
