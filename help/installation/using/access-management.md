---
product: campaign
title: 访问管理
description: 了解有关访问管理最佳实践的更多信息
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 8%

---

# 访问管理 {#access-management}



## Webapp操作员

webApp操作员是开箱即用的管理员。 要提高安全性，请遵循以下准则：

* 将此操作员中名为权限的管理员替换为新管理员（可以命名为“webapp”）。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 在文件夹（主要是收件人文件夹）中添加webApp运算符，以授予收件人读/写访问权限。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地域）实例，您可能希望将Web应用程序访问权限拆分到不同的收件人文件夹。 为实现此操作，请执行以下步骤：

   1. 复制webApp运算符

   1. 为每个重复项输入一个名称。 例如：webapp_brand、webapp_brand2等。

   1. 复制Web应用程序模板以让每个品牌拥有一个模板，并通过选择“使用特定帐户”来编辑属性以更改运算符。  请参阅[此页面](../../web/using/defining-web-forms-properties.md)以了解详情。

## 安全组和管理员操作员

创建足够的安全组，只向操作员授予足够的权利，让操作员能够执行所需操作，而不是执行更多操作。

请勿使用管理员运算符（或不共享它）。 为每个物理用户创建一个操作员（以便进行准确的审核/日志记录）。 将新命名的管理员添加到管理员组。 如果您不使用管理员运算符，请不要删除它，也不要禁用它：此运算符在内部用于执行处理。 但你可以禁止 [对客户端控制台的访问权限](../../platform/using/access-management.md) 并限制其安全区域（本地主机）。

避免在管理员组中添加过多操作员（或具有管理员命名权限）。 它们是功能非常强大的运算符（它们可以执行所有SQL语句，在服务器上执行命令等）。

Adobe Campaign通过以下方式提供三种高级别权限： [已命名权限](../../platform/using/access-management.md#named-rights)：

* **管理** （管理员）：提供对所有内容的访问权限并允许执行所有操作，绕过所有命名的权限检查，因此它包括PROGRAM EXECUTION (createProcess)和SQL命名权限

* **项目执行** (createProcess)：允许执行外部程序（在服务器上）

* **SQL**：允许对数据库运行SQL脚本（因此它可以绕过安全模型）。 注：如果需要执行复杂的计算（例如，过滤），可以要求数据库管理员创建一个SQL函数，并将它们添加到允许列表中。 请参阅[此页面](../../installation/using/scripting-coding-guidelines.md)以了解详情。

* **将其授予极少（且受信任的）操作员**
