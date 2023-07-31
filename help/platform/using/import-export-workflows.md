---
product: campaign
title: 使用工作流导入和导出数据
description: 了解如何使用Campaign中的工作流导入和导出数据
feature: Data Management, Workflows
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 31%

---

# 使用工作流导入和导出数据 {#import-export-workflows}



## 收集数据 {#collecting-data-workflows}

工作流程可以用来自动执行某些导入过程。无论是从本地文件还是从 SFTP 导入数据，都可以使用工作流程来标准化数据管理过程。

### 使用列表中的数据：读取列表 {#using-data-from-a-list--read-list}

工作流中发送的数据可以来自事先已准备并构建数据的列表。

此列表可能直接在Adobe Campaign中创建或由导入 **[!UICONTROL Import a list]** 选项。 有关此选项的更多信息，请参阅此 [页面](../../platform/using/about-generic-imports-exports.md).

有关在工作流中使用读取列表活动的更多信息，请参阅 [此页面](../../workflow/using/read-list.md).

### 从文件加载数据 {#loading-data-from-a-file}

可在工作流中处理的数据可从结构化文件中提取，以便将其导入Adobe Campaign。

有关加载数据活动的描述，请参阅 [数据加载（文件）](../../workflow/using/data-loading--file-.md) 部分。

要导入的结构化文件示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

收集数据后，您可以在工作流中使用该数据，例如，扩充投放或更新数据库。 有关详细信息，请参见[此页面](../../workflow/using/how-to-use-workflow-data.md)。

## 导出数据 {#exporting-data-via-a-workflow}

在使用可用于转换数据的一些可用数据管理活动之后，可以使用工作流程来自动执行某些导出过程或导出精确数据集。

使用执行导出操作 **[!UICONTROL Data extraction (file) activity]**. 有关如何配置和使用活动的更多信息，请参阅 [此页面](../../workflow/using/extraction--file-.md).
