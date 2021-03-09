---
solution: Campaign Classic
product: campaign
title: 访问管理
description: 了解有关访问管理最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 5%

---


# 访问管理 {#access-management}

## Webapp运营商

开箱即用，webApp运营商是管理员。 要提高安全性，请遵循以下准则：

* 将此运算符中直接命名的管理员替换为新管理员（可以命名为“webapp”）。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 在文件夹(主要是收件人文件夹)中添加webApp运算符，以授予对收件人的读/写访问权限。 有关详细信息，请参见[此页面](../../platform/using/access-management.md)。

* 如果使用多品牌（或多地域）实例，您可能希望将Web应用程序访问权限拆分为不同的收件人文件夹。 为实现此操作，请执行以下步骤：

   1. 重复webApp运营商

   1. 输入每个重复的名称。 例如：webapp_brand、webapp_brand2等。

   1. 重复一个Web应用程序模板，使每个品牌有一个模板，并通过选择使用特定帐户编辑属性以更改操作员。  请阅读[本页](../../web/using/defining-web-forms-properties.md)了解更多信息。

## 安全组和管理员操作员

创建足够的安全组，为运营商提供足够的权限，让运营商满足他们的需要，而非更多。

请勿使用管理员操作员（或不共享它）。 为每个实际用户创建一个操作员（以进行准确的审计/记录）。 将新命名的管理员添加到管理员组。 如果您不使用管理员操作员，请不要删除它，不要禁用它：此运算符用于内部执行处理。 但是，您可以禁止其[访问客户端控制台](../../platform/using/access-management.md)并限制其安全区域（到localhost）。

请避免在管理员组中添加过多操作员(或具有管理已命名权限)。 它们是非常强大的运算符（它们可以执行所有SQL语句，在服务器上执行命令等）。

Adobe Campaign通过[已命名权限](../../platform/using/access-management.md#named-rights)提供三个高级权限：

* **管理** （管理）：允许访问所有内容并允许执行所有操作，而忽略所有已命名的权利检查，因此它包括项目 EXECUTION(createProcess)和SQL已命名权限

* **项目执行** (createProcess):允许执行外部项目（在服务器上）

* **SQL**:允许在数据库上运行SQL脚本（以便它可以绕过安全模型）。注意：如果需要执行复杂计算（例如筛选），可以要求数据库管理员创建SQL函数并将其添加到允许列表。 请阅读[本页](../../installation/using/scripting-coding-guidelines.md)了解更多信息。

* **授予极少（并受信任）的运营商**
