---
solution: Campaign Classic
product: campaign
title: 数据导入和导出入门
description: 进一步了解Campaign Classic数据导入和导出。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 6%

---


# 开始数据导入和导出{#get-started-data-import-export}

Adobe Campaign Classic提供数据管理功能，允许您进出口数据。 这些操作可以使用工作流或通用导入和导出来执行。

>[!IMPORTANT]
>
>使用此功能时，请记住SFTP存储、存储库和活动用户档案限制，这些限制均应符合您的Adobe Campaign合同。

## 工作流 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工** 作流是实现导入流程自动化的有用方式。无论您是从本地文件导入数据，还是从SFTP导入数据，它们都允许您实现数据管理过程的标准化。

有了工作流，可以根据计划自动重复进出口操作，例如自动在多个信息系统之间交换数据。

如需详细信息，请参阅[此部分](../../platform/using/import-export-workflows.md)。

## 一般导入和导出 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

此外，Campaign Classic还提供&#x200B;**通用导入和导出**，允许您创建临时导入或导出作业。

导入和导出在专用模板中进行配置，您可以配置并使用这些模板来启动和监视导入和导出作业。

有关通用导入和导出的详细信息，请参阅[此部分](../../platform/using/about-generic-imports-exports.md)。

>[!IMPORTANT]
>通用导入和导出应仅用于临时操作。 为确保数据一致性并提高效率，建议使用工作流执行导入和导出操作。

## 数据加密和压缩{#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic允许您导入压缩或加密文件，并导出压缩或加密文件。

这些操作是在工作流内执行的，方法是将预处理阶段应用于要利用的数据。

有关更多信息，请参阅一下章节。

* [解压或解密文件](../../platform/using/unzip-decrypt.md)
* [压缩或加密文件](../../platform/using/zip-encrypt.md)

## 最佳实践和疑难解答{#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

执行导入和导出操作时应遵循几个[最佳实践](../../platform/using/import-export-best-practices.md)，以确保数据库内的数据一致性并避免在更新或导出过程中出现常见错误。

此外，[本节](../../platform/using/sftp-server-usage.md)还提供与SFTP服务器使用相关的建议和常见问题。
