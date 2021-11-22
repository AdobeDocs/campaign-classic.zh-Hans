---
product: campaign
title: 导入和导出最佳实践
description: 进一步了解导入或导出数据时要遵循的最佳实践。
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# 导入和导出最佳实践 {#import-export-best-practices}

![](../../assets/common.svg)

谨慎并遵循下面详述的几个简单规则，将有助于确保数据库内的数据一致性，并避免在数据库更新或数据导出期间出现常见错误。

## 使用工作流模板 {#using-import-templates}

大多数旨在导入数据的工作流应包含以下活动： **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

使用工作流模板可以非常方便地准备类似的导入，并确保数据库中的数据一致性。

在许多项目中，导入是在没有 **[!UICONTROL Deduplication]** 活动，因为项目中使用的文件没有重复项。 有时会从导入不同的文件中显示重复项。 因此，重复数据消除会很困难。 因此，在所有导入工作流中，重复数据删除步骤都是一种良好的预防措施。

请不要假定传入数据是一致且正确的，或者IT部门或Adobe Campaign主管将负责处理。 在项目期间，请牢记数据清理。 在导入数据时，删除重复项、协调并维护一致性。

有关专为导入数据而设计的通用工作流模板的示例，请参阅 [示例：用于导入数据的工作流模板](../../platform/using/creating-import-export-templates.md) 中。

## 使用平面文件格式 {#using-flat-file-formats}

导入的最有效格式是平面文件。 平面文件可以在数据库级别以批量模式导入。

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

## 使用压缩 {#using-compression}

尽可能使用压缩文件进行导入和导出。 默认支持GZIP。 您可以在导入文件时添加预处理，或在提取数据时添加后处理(分别在 **[!UICONTROL Load file]** 和 **[!UICONTROL Extract file]** 工作流活动。

**相关主题：**

* [数据加载（文件）活动](../../workflow/using/data-loading--file-.md)
* [数据提取（文件）活动](../../workflow/using/extraction--file-.md)

## 在增量模式下导入 {#importing-in-delta-mode}

必须在增量模式下进行常规导入。 这意味着每次只会向Adobe Campaign发送已修改或新数据，而不是整个表。

完全导入仅应用于初始加载。

## 保持一致性 {#maintaining-consistency}

要保持Adobe Campaign数据库中的数据一致性，请遵循以下原则：

* 如果导入的数据与Adobe Campaign中的引用表匹配，则应将其与工作流中的该表协调。 不匹配的记录应被拒绝。
* 确保导入的数据始终为 **&quot;标准化&quot;** （电子邮件、电话号码、直邮地址），且此标准化是可靠的，在几年内不会发生更改。 如果情况不同，数据库中可能会出现一些重复项，并且由于Adobe Campaign不提供用于执行“模糊”匹配的工具，因此很难管理和删除这些重复项。
* 事务型数据应具有协调键值并与现有数据协调，以避免创建重复项。
* **按顺序导入相关文件**. 如果导入由多个相互依赖的文件组成，则工作流应确保按正确顺序导入文件。 文件失败时，不会导入其他文件。
* **删除重复项**&#x200B;在导入数据时协调并保持一致性。
