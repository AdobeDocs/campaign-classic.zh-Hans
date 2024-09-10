---
product: campaign
title: 报告最佳实践
description: Campaign报告最佳实践
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 5%

---

# 报告最佳实践{#best-practices-reporting}



## 分析您的需求{#analyzing-needs}

使用报表工具取决于要处理的数据量、其复杂性以及要设置的报表类型。

要优化报告的创建、使用和持久性，您需要仔细考虑要满足的需求。 第一个分析将让您确定要创建的报告类型和最佳创建模式。 要创建报告，请应用以下步骤：

1. 确定需求

   第一步是明确确定需求：您希望在报告中显示的内容及其目标（监控、分析、数据导出等）。

   Adobe Campaign提供多种报表功能。 分析确定最合适功能的需要很重要。

   例如，您可以：

   * 浏览数据库中的数据并定义测量。 可在[此小节](../../reporting/using/ac-cubes.md)中了解详情。
   * 向现有报告添加指标。 可在[此小节](../../reporting/using/about-reports-creation-in-campaign.md)中了解详情。
   * 查看数据库中的数据。 可在[此小节](../../reporting/using/about-descriptive-analysis.md)中了解详情。
   * 创建新的投放报告。 在本节](../../reporting/using/about-reports-creation-in-campaign.md)中了解更多[，
   * 从Adobe Campaign数据库导出数据(通过工作流，请参阅[此部分](../../workflow/using/about-workflows.md)
   * 创建数据透视表。 可在[此小节](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)中了解详情。
   * 浏览汇总的数据。 可在[此小节](../../reporting/using/ac-cubes.md)中了解详情。
   * 使用助理分析数据。 可在[此小节](../../reporting/using/about-descriptive-analysis.md)中了解详情。
   * 分析大量数据。 可在[此小节](../../reporting/using/about-reports-creation-in-campaign.md)中了解详情。

1. 确定目标人群

   然后，您需要确定要创建的报告将定位谁，了解查看该报告的公众类型以及报告显示模式(在浏览器中、在Adobe Campaign中、针对特定对象、针对整个平台等)。

   您还可以为以下项创建报告：

   * 所有Adobe Campaign操作员，
   * 仅有权访问营销活动的操作员，
   * 一个操作员临时使用，
   * Web访问中的所有操作员等

   这些考虑因素还需要考虑到与访问权限和安全相关的问题。

1. 定义内容

   然后，您需要找到要显示的数据类型：投放指标、数据库用户档案报告等。

   您还需要了解此数据的性质（简单、由计算产生、重要程度等）、其位置(在Adobe Campaign中，位于第三方系统中)、用于定义计算周期的更新频率（每日、每周、实时）及其数量。

   与数据量和更新相关联的问题需要仔细研究，以避免报告显示问题，尤其是时间方面的问题。 因此，我们建议创建聚合，以便在报表之外预计算某些数据。 包含跟踪和投放日志的表可以包含数百万条记录：这意味着需要通过工作流聚合数据，才能在报表中使用这些数据。

## 优化报告设计{#optimizing-report-creation}

### 数据量 {#data-volume}

为了保证最佳性能，操作数据的数量不能太大。

即：

* 报表的计算时间不得超过5分钟。

  同样，在设计阶段，由于数据量较小，如果报告计算超过60秒，则需要改变计算方法。

* 使用Marketing Analytics模块时，报表数据不能超过1000万行。

我们还建议在夜间计算聚合，并在报表中直接使用此聚合数据。 必须通过专用数据管理工作流（SQL查询）创建这些聚合。

您还可以在夜间计算报表，并自动创建可随时查看的历史记录，而不会使数据库过载。

### 查询 {#queries}

我们建议尽可能使用SQL查询并避免JavaScript后处理。 如有必要，请在工作流中使用脚本活动，并删除用于计算的数据。 您还可以使用归档数据加快处理时间。

在这种情况下，应使用以下语法：

```
if(string(ctx@_historyId)!==""))
```

用于收集报表中显示的数据的查询不得过于复杂，尤其是应用到数据库中的所有数据时。 为了提高性能，在执行这些查询之前筛选数据可能很有用：这意味着计算将只涉及部分数据。

### 性能 {#performances}

通过以上建议，可优化报表计算。

除此之外，Adobe Campaign还建议进行以下改进：

* 使用数据模型：必须主要使用索引字段来改进计算公式。

  要快速查找已编制索引的字段，请在Adobe Campaign界面中查看列的名称：如果字段已编制索引，排序箭头将以红色加下划线。

  有关索引的更多信息，请参阅[此章节](../../configuration/using/data-model-best-practices.md#indexes)。

* 确保报告可扩展：数据量可能会随着时间的推移而显着增加。

  同样，在测试阶段处理的数据量可能与生产中的实际数据量不同。 这就是为什么测试阶段很重要。

  最后，需要知道数据清除延迟，并在必要时对其进行调整以方便数据操作。

  有关清理和数据保留的更多信息，请参阅[此部分](../../configuration/using/data-model-best-practices.md#data-retention)。

### 导出您的报告 {#exporting-reports}

[此部分](../../reporting/using/actions-on-reports.md#exporting-a-report)中详细介绍了特定于导出报告的Recommendations。
