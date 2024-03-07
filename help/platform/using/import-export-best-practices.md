---
product: campaign
title: 导入和导出最佳实践
description: 详细了解在导入或导出数据时应遵循的最佳实践
feature: Data Management
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 2%

---

# 导入和导出最佳实践 {#import-export-best-practices}



谨慎并遵循下面详述的几个简单规则，将有助于确保数据库内的数据一致性，并避免在数据库更新或数据导出期间出现常见错误。

## 使用工作流模板 {#using-import-templates}

大多数旨在导入数据的工作流应包含以下活动： **[!UICONTROL Load file]**， **[!UICONTROL Reconciliation]**， **[!UICONTROL Segmentation]**， **[!UICONTROL Deduplication]**， **[!UICONTROL Update data]**.

使用工作流模板可以非常方便地准备类似的导入并确保数据库内的数据一致性。

在许多项目中，导入是在没有 **[!UICONTROL Deduplication]** 活动，因为项目中使用的文件没有重复项。 导入不同文件时有时会出现重复项。 然后，重复数据消除就变得非常困难。 因此，在所有导入工作流中，重复数据删除步骤都是很好的预防措施。

请勿假定传入的数据是一致和正确的，或者IT部门或Adobe Campaign主管会处理此数据。 在项目进行期间，请牢记数据清理。 在导入数据时执行重复数据删除、协调和维护一致性。

有关为导入数据而设计的通用工作流模板的示例，请参阅 [示例：用于导入数据的工作流模板](../../platform/using/creating-import-export-templates.md) 部分。

## 使用平面文件格式 {#using-flat-file-formats}

最有效的导入格式是平面文件。 可以在数据库级别以批量模式导入平面文件。

例如：

* 分隔符：制表符或分号
* 带有标题的第一行
* 无字符串分隔符
* 日期格式： `YYYY/MM/DD HH:mm:SS`

要导入的文件示例：

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## 使用压缩 {#using-compression}

尽可能将压缩文件用于导入和导出。 默认支持GZIP。 在导入文件时，可添加预处理；在提取数据时，可添加后处理，分别位于 **[!UICONTROL Load file]** 和 **[!UICONTROL Extract file]** 工作流活动。

**相关主题：**

* [数据加载（文件）活动](../../workflow/using/data-loading-file.md)
* [数据提取（文件）活动](../../workflow/using/extraction-file.md)

## 在增量模式下导入 {#importing-in-delta-mode}

常规导入必须在增量模式下完成。 这意味着只向Adobe Campaign发送修改的数据或新数据，而不是每次都发送整个表。

完全导入只应用于初始加载。

## 保持一致性 {#maintaining-consistency}

要维护Adobe Campaign数据库中的数据一致性，请遵循以下原则：

* 如果导入的数据与Adobe Campaign中的引用表匹配，则应将其与工作流中的该表进行协调。 应拒绝不匹配的记录。
* 确保导入的数据始终 **“已标准化”** （电子邮件、电话号码、直邮地址），并且此标准化是可靠的，并且不会随着时间推移而改变。 如果不是这种情况，数据库中可能会出现一些重复项，并且由于Adobe Campaign不提供进行“模糊”匹配的工具，因此将很难管理和删除它们。
* 事务型数据应具有协调键值，并与现有数据进行协调，以避免创建重复项。
* **按顺序导入相关文件**. 如果导入由多个相互依赖的文件组成，则工作流应确保这些文件按正确的顺序导入。 当文件失败时，不会导入其他文件。
* **删除重复项**，在导入数据时协调并保持一致性。
