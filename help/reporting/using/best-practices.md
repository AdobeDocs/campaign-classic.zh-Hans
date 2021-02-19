---
solution: Campaign Classic
product: campaign
title: 报告最佳实践
description: 活动 报告最佳做法
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---


# 报告最佳实践{#best-practices-reporting}

## 分析需求{#analyzing-needs}

使用报告工具取决于要处理的报告量、其复杂性和要设置的数据类型。

要优化报表的创建、使用和耐用性，您需要仔细查看您想要满足的需求。 第一个分析将允许您确定要创建的报告类型和最佳创建模式。 要创建报表，请应用以下步骤：

1. 确定需求

   第一步是明确确定需求：您希望在报表中显示的内容及其目标(监控、分析、数据导出等)。

   Adobe Campaign优惠各种报告能力。 分析您确定最合适功能的需求非常重要。

   例如，您可以：

   * 浏览数据库中的数据并定义测量。 了解本节](../../reporting/using/about-cubes.md)中的更多信息[
   * 向现有报表添加指标。 了解本节](../../reporting/using/about-reports-creation-in-campaign.md)中的更多信息[
   * 视图数据库中的数据。 了解本节](../../reporting/using/about-descriptive-analysis.md)中的更多信息[
   * 新建投放报表。 了解有关本节](../../reporting/using/about-reports-creation-in-campaign.md)的更多信息，[
   * 从Adobe Campaign数据库导出数据(通过工作流，请参阅[本节](../../workflow/using/about-workflows.md)
   * 创建透视表。 了解本节](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)中的更多信息[
   * 浏览聚合数据。 了解本节](../../reporting/using/about-cubes.md)中的更多信息[
   * 使用向导分析数据。 了解本节](../../reporting/using/about-descriptive-analysis.md)中的更多信息[
   * 分析大量数据。 了解本节](../../reporting/using/about-reports-creation-in-campaign.md)中的更多信息[

1. 确定目标群

   然后，您需要了解要创建的报表将目标的人、将视图报表的公众类型以及报表显示模式(在Adobe Campaign中、在中、针对特定对象、针对整个平台等)。

   您还可以为以下对象创建报表：

   * 所有Adobe Campaign运算符，
   * 仅有权访问营销活动、
   * 一个操作员，
   * Web访问等中的所有操作符

   这些考虑因素还需要考虑与访问权和安全有关的问题。

1. 定义内容

   然后，您需要了解要显示的数据类型：投放指示器、有关数据库用户档案的报告等。

   您还需要了解此数据的性质（简单，由计算、重要等所导致）、其位置(在Adobe Campaign中，在第三方系统中)、其定义计算周期的更新频率（每日、每周、实时）以及其音量。

   需要仔细研究与数据卷和更新相关的问题，以避免报告显示问题，特别是在时间方面。 因此，我们建议创建聚合以预计报表外的一些数据。 包含跟踪和投放日志的表可以包含数百万条记录：这意味着需要通过要在报表中使用的工作流来聚合数据。

## 优化报表创建{#optimizing-report-creation}

### 数据卷{#data-volume}

为保证最佳性能，操作数据量不能太大。

即：

* 报告的计算时间不得超过5分钟。

   同样，在设计阶段，如果报告计算超过60秒，则需要更改计算方法。

* 使用Marketing Analytics模块时，报告数据不得超过1000万行。

我们还建议在晚上计算聚合，并在报告中直接使用此汇总数据。 这些聚合必须通过专用数据管理工作流(SQL查询)创建。

您还可以在夜间计算报告并自动创建历史记录，该历史记录可以随时查看，而不会使数据库过载。

### 查询{#queries}

我们建议尽可能使用SQL查询，并避免JavaScript后处理。 如有必要，请在工作流中使用脚本活动并删除用于计算的数据。 您还可以使用归档数据来加快处理时间。

在这种情况下，应使用以下语法：

```
if(string(ctx@_historyId)!==""))
```

使您能够收集报告中显示的数据的查询不应太复杂，尤其是应用于数据库中的所有数据时。 要提高性能，在执行以下查询之前过滤数据可能很有用：这意味着计算只涉及部分数据。

### 性能{#performances}

上述建议使您能够优化报表计算。

除此之外，Adobe Campaign还建议进行以下改进：

* 处理您的数据模型：索引字段必须主要用于改进计算公式。

   要快速查找索引字段，请查看Adobe Campaign界面中列的名称：如果对字段进行索引，排序箭头将以红色加下划线。

   有关索引的详细信息，请参阅[本节](../../configuration/using/data-model-best-practices.md#indexes)。

* 确保报表可伸缩：数据量可能会随着时间的推移而显着增加。

   同样，在测试阶段期间操作的数据量可能不同于生产中的实际数据量。 这就是测试阶段很重要的原因。

   最后，需要了解并调整数据清除延迟，以便轻松进行数据操作。

   有关清理和数据保留的详细信息，请参阅[本节](../../configuration/using/data-model-best-practices.md#data-retention)。

### 导出报告{#exporting-reports}

特定于导出报表的Recommendations在[本节](../../reporting/using/actions-on-reports.md#exporting-a-report)中有详细说明。
