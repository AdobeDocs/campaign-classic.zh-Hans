---
product: campaign
title: 报告最佳实践
description: Campaign报告最佳实践
feature: Reporting
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 报表最佳实践{#best-practices-reporting}

![](../../assets/common.svg)

## 分析您的需求{#analyzing-needs}

使用报告工具取决于要处理的数据量、其复杂性以及要设置的报告类型。

要优化报表的创建、使用和持久性，您需要仔细查看您想要满足的需求。 通过第一个分析，您可以确定要创建的报表类型和最佳创建模式。 要创建报表，请应用以下步骤：

1. 确定需求

   第一步是明确需求：您希望在报表中显示的内容及其目标（监控、分析、数据导出等）。

   Adobe Campaign提供多种报告能力。 分析确定最合适功能的需求非常重要。

   例如，您可以：

   * 浏览数据库中的数据并定义测量。 了解更多 [在此部分中](../../reporting/using/about-cubes.md)
   * 将指标添加到现有报表。 了解更多 [在此部分中](../../reporting/using/about-reports-creation-in-campaign.md)
   * 查看数据库中的数据。 了解更多 [在此部分中](../../reporting/using/about-descriptive-analysis.md)
   * 创建新投放报告。 了解更多 [在此部分中](../../reporting/using/about-reports-creation-in-campaign.md))、
   * 从Adobe Campaign数据库导出数据(通过工作流，请参阅 [此部分](../../workflow/using/about-workflows.md)
   * 创建数据透视表。 了解更多 [在此部分中](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * 浏览聚合数据。 了解更多 [在此部分中](../../reporting/using/about-cubes.md)
   * 使用向导分析数据。 了解更多 [在此部分中](../../reporting/using/about-descriptive-analysis.md)
   * 分析大量数据。 了解更多 [在此部分中](../../reporting/using/about-reports-creation-in-campaign.md)

1. 确定目标群体

   然后，您需要了解要创建的报表针对的对象，了解将查看报表的公众类型以及报表显示模式(在浏览器、Adobe Campaign、特定对象、整个平台等中)。

   您还可以为以下对象创建报表：

   * 所有Adobe Campaign操作员，
   * 仅具有访问营销活动权限的操作员，
   * 一个用于临时使用的运算符，
   * Web访问等中的所有运算符。

   这些考虑事项还需要考虑与访问权限和安全性相关的问题。

1. 定义内容

   然后，您需要确定要显示的数据类型：投放指标、数据库用户档案报告等。

   您还需要了解此数据的性质（由计算、显着性等所导致的简单数据）、其位置(在Adobe Campaign中，位于第三方系统中)、其定义计算周期的更新频率（每日、每周、动态）以及其数量。

   需要仔细研究与数据卷和更新相关的问题，以避免报告显示问题，特别是在时间方面的问题。 因此，我们建议创建聚合以在报表外预算一些数据。 包含跟踪和投放日志的表可以包含数百万条记录：这意味着需要通过要在报表中使用的工作流来聚合数据。

## 优化报表设计{#optimizing-report-creation}

### 数据卷 {#data-volume}

为保证最佳性能，操作数据量不能太大。

即：

* 报表的计算时间不得超过5分钟。

   同样，在设计阶段，如果报告计算超过60秒，则在数据量较小的情况下，需要更改计算方法。

* 使用Marketing Analytics模块时，报表数据不得超过1000万行。

我们还建议在晚上计算聚合，并在报告中直接使用此聚合数据。 这些聚合必须通过专用的数据管理工作流（SQL查询）创建。

您还可以在夜间计算报告，并自动创建可以随时查看的历史记录，而不会使数据库过载。

### 查询 {#queries}

我们建议尽可能使用SQL查询，并避免JavaScript后处理。 如有必要，请在工作流中使用脚本活动，并删除用于计算的数据。 您还可以使用存档数据来加快处理时间。

在这种情况下，应使用以下语法：

```
if(string(ctx@_historyId)!==""))
```

使您能够收集报告中显示的数据的查询不得过于复杂，尤其是当查询应用于数据库中的所有数据时。 为了提高性能，在执行这些查询之前筛选数据会非常有用：这意味着计算将仅涉及部分数据。

### 性能 {#performances}

通过上述建议，您可以优化报表计算。

除此之外，Adobe Campaign还建议进行以下改进：

* 使用您的数据模型：索引字段必须主要用于改进计算公式。

   要快速查找索引字段，请查看Adobe Campaign界面中列的名称：如果字段已编入索引，则排序箭头的下划线为红色。

   有关索引的更多信息，请参阅 [此部分](../../configuration/using/data-model-best-practices.md#indexes).

* 确保报表可缩放：数据量会随着时间的推移而显着增加。

   同样，在测试阶段期间操作的数据量可能与生产中的实际数据量不同。 这就是测试阶段很重要的原因。

   最后，需要知道并调整数据清除延迟，以便于进行数据操作。

   有关清理和数据保留的更多信息，请参阅 [此部分](../../configuration/using/data-model-best-practices.md#data-retention).

### 导出报表 {#exporting-reports}

Recommendations中详细介绍了特定于导出报表的 [此部分](../../reporting/using/actions-on-reports.md#exporting-a-report).
