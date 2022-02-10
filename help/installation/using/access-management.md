---
product: campaign
title: 访问管理
description: 了解有关访问管理最佳实践的更多信息
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 8%

---

# 访问管理 {#access-management}

![](../../assets/v7-only.svg)

## Web应用程序操作员

webApp操作员是管理员。 要提高安全性，请遵循以下准则：

* 将此运算符中名为的管理员替换为新管理员（可以命名为“webapp”）。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 在文件夹（主要是收件人文件夹）中添加webApp运算符，以授予收件人的读/写访问权限。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地域）实例，您可能希望将Web应用程序访问权限拆分到不同的收件人文件夹。 为实现此操作，请执行以下步骤：

   1. 复制webApp运算符

   1. 输入每个副本的名称。 例如：webapp_brand、webapp_brand2等。

   1. 复制Web应用程序模板以在每个品牌中有一个模板，并通过选择使用特定帐户来编辑属性以更改运算符。  请参阅[此页面](../../web/using/defining-web-forms-properties.md)以了解详情。

## 安全组和管理员操作员

创建足够的安全组，仅为操作员授予足够的权限，让操作员能够执行所需操作，而不是执行更多操作。

请勿使用管理员运算符（或不共享它）。 为每个实际用户创建一个运算符（以进行准确的审核/记录）。 将新命名的管理员添加到管理员组。 如果您不使用管理员运算符，请不要删除它，也不要禁用它：此运算符用于内部执行处理。 但你可以禁止它 [访问客户端控制台](../../platform/using/access-management.md) 并将其安全区域（限制为本地主机）。

避免在管理员组中添加过多的运算符（或者具有管理员命名权限的运算符）。 它们是非常强大的运算符（它们可以执行所有SQL语句、在服务器上执行命令等）。

Adobe Campaign通过 [已命名权限](../../platform/using/access-management.md#named-rights):

* **管理** （管理员）：允许访问所有内容，并允许执行所有操作，而无需进行所有命名的权限检查，因此它包括PROGRAM EXECUTION(createProcess)和SQL命名权限

* **程序执行** (createProcess):允许执行外部程序（在服务器上）

* **SQL**:允许在数据库上运行SQL脚本（以便绕过安全模型）。 注意：如果需要执行复杂的计算（例如过滤），可以请求数据库管理员创建SQL函数并将其添加到该允许列表。 请参阅[此页面](../../installation/using/scripting-coding-guidelines.md)以了解详情。

* **授予极少（且受信任）的运算符**
