---
solution: Campaign Standard
product: campaign
title: 导入和导出最佳实践
description: 了解有关导入或导出数据时要遵循的最佳实践的更多信息。
audience: automating
content-type: reference
topic-tags: workflow-general-operation
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 2%

---


# 导入和导出最佳实践 {#import-export-best-practices}

谨慎并遵循下面详述的几个简单规则将大大有助于确保数据库中的数据一致性，并避免在数据库更新或数据导出期间出现常见错误。

## 使用工作流模板{#using-import-templates}

大多数旨在导入数据的工作流应包含以下活动:**[!UICONTROL Load file]**、**[!UICONTROL Reconciliation]**、**[!UICONTROL Segmentation]**、**[!UICONTROL Deduplication]**、**[!UICONTROL Update data]**。

使用工作流模板可以非常方便地准备类似的导入并确保数据库中的数据一致性。

在许多项目中，导入构建时没有&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动，因为项目中使用的文件没有重复。 重复有时会从导入不同的文件中显示。 因此，重复数据消除很困难。 因此，外部重复数据删除步骤是所有导入工作流中的一个良好预防措施。

切勿假定传入数据是一致和正确的，或IT部门或Adobe Campaign主管将负责处理。 在项目过程中，请牢记数据清理。 在导入数据时消除重复、协调并维护一致性。

[示例中提供了为导入数据而设计的通用工作流模板的示例：用于导入数据](../../platform/using/creating-import-export-templates.md)部分的工作流模板。

## 使用平面文件格式{#using-flat-file-formats}

导入的最有效格式是平面文件。 可以在数据库级别以批量模式导入平面文件。

例如：

* 分隔符：制表符或分号
* 带标题的第一行
* 无字符串分隔符
* 日期格式：YYYY/MM/DD HH:mm:SS

要导入的文件示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 使用压缩{#using-compression}

尽可能使用压缩文件进行导入和导出。 默认支持GZIP。 您可以分别在&#x200B;**[!UICONTROL Load file]**&#x200B;和&#x200B;**[!UICONTROL Extract file]**&#x200B;工作流活动中添加导入文件时的预处理或提取数据时的后处理。

**相关主题：**

* [数据加载（文件）活动](../../workflow/using/data-loading--file-.md)
* [数据提取（文件）活动](../../workflow/using/extraction--file-.md)

## 在增量模式{#importing-in-delta-mode}中导入

必须在增量模式下执行常规导入。 这意味着每次只向Adobe Campaign发送修改或新数据，而不是整个表。

完全导入应仅用于初始加载。

## 维护一致性{#maintaining-consistency}

要保持Adobe Campaign数据库中的数据一致性，请遵循以下原则：

* 如果导入的数据与Adobe Campaign中的引用表匹配，则应将其与工作流中的该表协调。 不匹配的记录应被拒绝。
* 确保导入的数据始终&#x200B;**&quot;normalized&quot;**（电子邮件、电话号码、直接邮件地址），并且此规范是可靠的，并且多年内不会更改。 如果不是这样，某些重复可能会出现在数据库中，而由于Adobe Campaign不提供进行“模糊”匹配的工具，因此很难管理和删除它们。
* 事务数据应具有合并关键项并与现有数据协调，以避免创建重复。
* **按顺序导入相关文件**。如果导入由多个相互依赖的文件组成，则工作流应确保以正确的顺序导入文件。 文件失败时，不导入其他文件。
* **在导入数据**&#x200B;时，消除重复、协调并维护一致性。
