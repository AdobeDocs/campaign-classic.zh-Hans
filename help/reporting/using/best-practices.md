---
title: 报告的最佳实践
seo-title: 报告的最佳实践
description: 报告的最佳实践
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# 报告的最佳实践{#best-practices-reporting}

## 分析需求{#analyzing-needs}

使用报告工具取决于要处理的数据量、其复杂性以及要设置的报告类型。

要优化报表的创建、使用和耐用性，您需要仔细查看您想要满足的需求。 第一项分析将使您能够确定要创建的报告类型和最佳创建模式。 要创建报告，请应用以下步骤：

1. 确定需求

   第一步是明确确定需求：您希望在报告中显示的内容及其目标（监控、分析、数据导出等）。

   Adobe Campaign提供各种报告功能。 分析您需要识别最合适的功能，这一点很重要。

   例如，您可以：

   * 浏览数据库中的数据并定义测量值(通 [过本节](../../reporting/using/about-cubes.md)),
   * 向现有报告添加指示器(请参 [阅本节](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 查看数据库中的数据(通 [过本节](../../reporting/using/about-descriptive-analysis.md)),
   * 创建新的交付报告(请参 [阅本节](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 从Adobe Campaign数据库导出数据(通过工作流，请参 [阅本节](../../workflow/using/about-workflows.md)),
   * 创建透视表(请参 [阅本节](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * 浏览汇总数据(通 [过本节](../../reporting/using/about-cubes.md)),
   * 使用向导分析数据(通过此 [部分](../../reporting/using/about-descriptive-analysis.md)),
   * 分析大量数据(请参 [阅本节](../../reporting/using/about-reports-creation-in-campaign.md))等。

1. 确定目标人群

   然后，您需要了解要创建的报表的目标对象，了解将查看该报表的公共类型以及报表显示模式（在浏览器中、Adobe Campaign中、特定对象中、整个平台等）。

   您还可以为以下对象创建报告：

   * 所有Adobe Campaign运营商、
   * 仅有权访问营销活动的运营商，
   * 一个临时使用的操作员，
   * Web访问等中的所有运营商
   这些注意事项还需要考虑与访问权限和安全性相关的问题。

1. 定义内容

   然后，您需要了解要显示的数据类型：交付指标、有关数据库配置文件的报告等。

   您还需要了解此数据的性质（由计算、重要等引起的简单）、其位置（在Adobe Campaign中，在第三方系统中）、其更新频率以定义计算周期（每日、每周、实时）以及其音量。

   需要仔细研究与数据卷和更新相关的问题，以避免报告显示问题，特别是在时间方面。 因此，我们建议创建聚合以预计报表外的一些数据。 包含跟踪和交付日志的表可以包括数百万条记录：这意味着需要通过要在报表中使用的工作流来聚集数据。

## 优化报告创建{#optimizing-report-creation}

### 数据卷 {#data-volume}

为了保证最佳性能，操作数据量不能太大。

即：

* 报告的计算时间不得超过5分钟。

   同样，在设计阶段，如果报告计算超过60秒，则需要改变计算方法。

* 使用Marketing Analytics时，被操纵的数据不能超过1000万行。

我们还建议在夜间计算汇总，并在报告中直接使用此汇总数据。 这些聚合必须通过专用的数据管理工作流（SQL查询）创建。

您还可以在夜间计算报告，并自动创建可随时查看的历史记录，而不会使数据库过载。

### 查询 {#queries}

我们建议尽可能使用SQL查询并避免JavaScript后期处理。 如有必要，请在工作流中使用脚本活动并删除用于计算的数据。 您还可以使用归档数据来加快处理时间。

在这种情况下，应使用以下语法：

```
if(string(ctx@_historyId)!==""))
```

允许您收集报告中显示的数据的查询不能过于复杂，尤其是当应用于数据库中的所有数据时。 为了提高性能，在执行这些查询之前过滤数据可能很有用：这意味着计算只涉及部分数据。

### 性能 {#performances}

上述建议使您能够优化报表计算。

除此之外，Adobe Campaign还建议进行以下改进：

* 研究数据模型：索引字段必须主要用于改进计算公式。

   要快速查找索引字段，请在Adobe Campaign界面中查看列的名称：如果已索引字段，则排序箭头的下划线为红色。

* 确保报表长期有效：数据量可能随着时间的推移而显着增加。

   类似地，在测试阶段期间操作的数据量可能不同于生产中的实际数据量。 这就是测试阶段很重要的原因。

   最后，需要知道并调整数据清除延迟以便轻松处理数据。

### 导出报告 {#exporting-reports}

本节详细介绍了特定于导出报告 [的建议](../../reporting/using/actions-on-reports.md#exporting-a-report)。
