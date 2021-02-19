---
solution: Campaign Classic
product: campaign
title: 使用工作流导入和导出数据
description: 了解如何使用Campaign Classic中的工作流导入和导出数据。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 34%

---


# 使用工作流导入和导出数据 {#import-export-workflows}

## 收集数据{#collecting-data-workflows}

工作流程可以用来自动执行某些导入过程。无论是从本地文件还是从 SFTP 导入数据，都可以使用工作流程来标准化数据管理过程。

### 使用列表中的数据：读取列表{#using-data-from-a-list--read-list}

在工作流中发送的数据可以来自列表，据此数据已预先准备和结构化。

此列表可能是在Adobe Campaign中直接创建的，或是通过&#x200B;**[!UICONTROL Import a list]**&#x200B;选项导入的。 有关此选项的详细信息，请参阅此[页面](../../platform/using/about-generic-imports-exports.md)。

有关在工作流中使用读取列表活动的详细信息，请参阅[此页面](../../workflow/using/read-list.md)。

### 从文件{#loading-data-from-a-file}加载数据

可以从结构化文件中提取工作流中处理的数据，以便将其导入Adobe Campaign。

在[数据加载（文件）](../../workflow/using/data-loading--file-.md)部分可找到加载数据活动的说明。

要导入的结构化文件示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

收集数据后，您可以在工作流中使用它，例如丰富投放或更新数据库。 有关详细信息，请参见[此页面](../../workflow/using/how-to-use-workflow-data.md)。

## 导出数据 {#exporting-data-via-a-workflow}

在使用可用于转换数据的一些可用数据管理活动之后，可以使用工作流程来自动执行某些导出过程或导出精确数据集。

使用&#x200B;**[!UICONTROL Data extraction (file) activity]**&#x200B;执行导出操作。 有关如何配置和使用活动的详细信息，请参阅[此页面](../../workflow/using/extraction--file-.md)。
