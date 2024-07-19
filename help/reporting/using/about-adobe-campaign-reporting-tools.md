---
product: campaign
title: 关于Adobe Campaign报表工具
description: 在内置报告或自定义报告中分析您的营销活动是否取得成功
feature: Reporting, Monitoring
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 18%

---

# 报告入门 {#about-adobe-campaign-reporting-tools}



除了[内置报告](../../reporting/using/about-campaign-built-in-reports.md)之外，Adobe Campaign还允许您在不同的上下文中生成报告，以满足不同的需求。 本文档详细介绍了使用原则和实施模式。

Adobe Campaign不是专门用于报表的工具：在Adobe Campaign中创建的报表主要允许您查看汇总的数据。 专门用于分析和表示数据的Adobe Campaign报表不用于数据库导出。

要从Adobe Campaign数据库导出数据，您需要创建工作流并使用数据导出活动。 如需详细信息，请参阅[此小节](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供了多种报表工具：

1. **内置报告**： Adobe Campaign提供了一组关于投放、营销策划、平台活动、可选功能等的报告。 这些报告可通过它们相关的各种功能获取。 它们可以根据您的特定需求进行调整。

   如需详细信息，请参阅[此小节](../../reporting/using/about-campaign-built-in-reports.md)。

1. **描述性数据分析**： Adobe Campaign提供了一个可视化的工具，用于生成有关数据库中数据的统计信息。 您可以使用专用向导创建描述性分析报告，并根据需要调整其内容和布局。

   如需详细信息，请参阅[此小节](../../reporting/using/about-descriptive-analysis.md)。

1. **个性化报表**：通过Adobe Campaign，您可以创建有关数据库中数据的报表。 创建这些组件后，即可在相应的上下文中访问它们。

   根据查询、计算和卷的复杂性，这些报告中分析的数据可以通过查询收集，并在列表（“数据管理”类型工作流）或多维数据集（使用Marketing Analytics）中进行预聚合。 它将以透视表或组列表的形式显示。

   如需详细信息，请参阅[此小节](../../reporting/using/about-reports-creation-in-campaign.md)。

1. **分析报表**： Marketing Analytics支持直观的数据探索。

   如需详细信息，请参阅[此小节](../../reporting/using/ac-cubes.md)。

>[!CAUTION]
>
>为了便于显示和操作以及高效的导出，报表中的行数不能超过1,000行。
