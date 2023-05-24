---
product: campaign
title: 关于Adobe Campaign报表工具
description: 在内置报告或自定义报告中分析您的营销活动是否取得成功
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 19%

---

# 开始使用报告 {#about-adobe-campaign-reporting-tools}



除此之外 [内置报告](../../reporting/using/about-campaign-built-in-reports.md)，通过Adobe Campaign可在各种上下文中生成报表并满足各种需求。 本文档详细介绍了使用原则和实施模式。

Adobe Campaign不是专门用于报表的工具：在Adobe Campaign中创建的报表主要为让您查看汇总的数据。 专门用于分析和表示数据的Adobe Campaign报表不用于数据库导出。

要从Adobe Campaign数据库导出数据，您需要创建工作流并使用数据导出活动。 如需详细信息，请参阅[此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供了多种报表工具：

1. **内置报告**：Adobe Campaign提供了一组关于投放、营销策划、平台活动、可选功能等的报告。 这些报告可通过其相关的各种功能获取。 它们可以根据您的特定需求进行调整。

   如需详细信息，请参阅[此部分](../../reporting/using/about-campaign-built-in-reports.md)。

1. **描述性分析**：Adobe Campaign提供了一个可视化工具，用于生成有关数据库中数据的统计信息。 您可以使用专用向导创建描述性分析报告，并根据需要调整其内容和布局。

   如需详细信息，请参阅[此部分](../../reporting/using/about-descriptive-analysis.md)。

1. **个性化报表**：通过Adobe Campaign可创建有关数据库中数据的报表。 创建这些组件后，即可在相应的上下文中访问它们。

   根据查询、计算和卷的复杂性，这些报告中分析的数据可以通过查询收集，并在列表（“数据管理”类型工作流）或多维数据集（使用Marketing Analytics）中预聚合。 它将以数据透视表或组列表的形式显示。

   如需详细信息，请参阅[此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. **分析报表**：借助Marketing Analytics，您可以直观地探索数据。

   如需详细信息，请参阅[此部分](../../reporting/using/ac-cubes.md)。

>[!CAUTION]
>
>为了便于显示和操作以及高效的导出，报表中的行数不能超过1,000行。
