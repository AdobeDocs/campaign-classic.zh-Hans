---
solution: Campaign Classic
product: campaign
title: 权限入门
description: 了解如何授予对活动功能的访问权限
feature: 访问管理
role: 业务从业者，管理员
level: 初学者
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 2%

---


# 开始使用权限{#access-management}

Adobe Campaign允许您定义和管理分配给各种运算符的权限。 这些权利和限制授权或拒绝：

* 访问某些功能(通过已命名权限),
* 访问某些记录，
* 创建、修改和/或删除记录(操作、联系人、活动、组等)。

权限适用于操作员用户档案或操作员组。

这些安全参数通过链接到操作员与Adobe Campaign的连接模式来完成。 有关[中安全区域的详细信息，请参阅此页](../../installation/using/security-zones.md)。

有两种类型的权限可以授予用户：

* 您可以定义对其赋予权限的操作员组，然后将运算符与一个或多个组关联。 这使您能够重复使用权限并使运营商用户档案更加一致。 它还方便了用户档案的管理和维护。 组创建和管理显示在[本节](access-management-groups.md)中。

* 您可以将已命名权限直接归因给用户，在某些情况下，这会使通过组分配的权限过载。 这些权限显示在[此页](access-management-named-rights.md)中。

>[!NOTE]
>
>在开始定义权限之前，Adobe建议您阅读[安全配置清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html)。

了解如何在以下部分授予访问权限和设置权限：

* [创建运算符](access-management-operators.md)

* [定义用户组](access-management-groups.md)

* [添加已命名权限](access-management-named-rights.md)

* [管理活动文件夹访问](access-management-folders.md)

* [访问权限矩阵](access-management-named-rights.md#access-rights-matrix)


另请参阅：

* [管理工作流权限](../../workflow/using/managing-rights.md)
* [管理分布式营销的权限](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [管理交互模块的权限](../../interaction/using/operator-profiles.md)
* [过滤对模式的访问](../../configuration/using/filtering-schemas.md)
* [限制PI视图](../../configuration/using/restricting-pii-view.md)
