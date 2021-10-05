---
product: campaign
title: 数据导入和导出入门
description: 进一步了解数据导入和导出的Campaign Classic。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 11%

---

# 数据导入和导出入门 {#get-started-data-import-export}

![](../../assets/common.svg)

Adobe Campaign Classic提供数据管理功能，允许您导入和导出数据。 可以使用工作流或通用导入和导出来执行这些操作。

>[!IMPORTANT]
>
>使用此功能时，请牢记SFTP存储、数据库存储和活动配置文件限制，这些限制均符合您的Adobe Campaign合同。

## 工作流 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**** 工作流是自动执行导入流程的有用方法。无论您是从本地文件还是从SFTP导入数据，它们都允许您标准化数据管理过程。

使用工作流，可以根据计划自动重复导入和导出操作，例如在多个信息系统之间自动交换数据。

如需详细信息，请参阅[此部分](../../platform/using/import-export-workflows.md)。

## 一般导入和导出 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

此外，Campaign Classic还提供&#x200B;**通用导入和导出**，允许您创建临时导入或导出作业。

导入和导出在专用模板中进行配置，您可以配置和使用这些模板来启动和监视导入和导出作业。

有关一般导入和导出的更多信息，请参阅[此部分](../../platform/using/about-generic-imports-exports.md)。

>[!IMPORTANT]
>一般导入和导出仅应用于临时操作。 为确保数据一致性并提高效率，建议使用工作流执行导入和导出操作。

## 数据加密和压缩 {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic允许您导入压缩或加密文件，以及导出压缩或加密文件。

这些操作是在工作流中执行的，方法是将预处理阶段应用于要利用的数据。

有关更多信息，请参阅一下章节。

* [解压缩或解密文件](../../platform/using/unzip-decrypt.md)
* [Zip或加密文件](../../platform/using/zip-encrypt.md)

## 最佳实践和故障排除 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

执行导入和导出操作时，您应遵循几个[最佳实践](../../platform/using/import-export-best-practices.md)，以确保数据库中的数据一致性，并避免在更新或导出操作期间出现常见错误。

此外，[此部分](../../platform/using/sftp-server-usage.md)中还提供了与SFTP服务器使用相关的建议和常见问题。
