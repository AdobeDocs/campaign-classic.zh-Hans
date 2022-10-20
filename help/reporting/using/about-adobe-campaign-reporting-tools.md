---
product: campaign
title: 关于Adobe Campaign报告工具
description: 在内建或自定义报告中，分析促销活动成功与否。
feature: Reporting
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 19%

---

# 开始使用报告 {#about-adobe-campaign-reporting-tools}

![](../../assets/common.svg)

除 [内置报告](../../reporting/using/about-campaign-built-in-reports.md)，则Adobe Campaign允许您在各种上下文中生成报表以满足不同的需求。 本文档详细介绍了使用原则和实施模式。

Adobe Campaign不是专门的报告工具：在Adobe Campaign中创建的报表主要允许您查看汇总的数据。 Adobe Campaign报告专门用于分析和表示数据，但并非为数据库导出而设计。

要从Adobe Campaign数据库导出数据，您需要创建工作流并使用数据导出活动。 如需详细信息，请参阅[此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供了多种报表工具：

1. **内置报告**:Adobe Campaign提供有关投放、营销策划、平台活动、可选功能等的一组报告。 这些报告通过与之相关的各种功能提供。 它们可以根据您的特定需求进行调整。

   如需详细信息，请参阅[此部分](../../reporting/using/about-campaign-built-in-reports.md)。

1. **描述性数据分析**:Adobe Campaign提供了一个可视化工具，用于生成有关数据库中数据的统计信息。 您可以使用专用向导创建描述性分析报告，并根据需要调整其内容和布局。

   如需详细信息，请参阅[此部分](../../reporting/using/about-descriptive-analysis.md)。

1. **个性化报表**:Adobe Campaign允许您创建数据库中数据的报告。 创建这些权限后，即可在相应的上下文中访问它们。

   根据查询、计算和卷的复杂性，可以通过查询收集这些报表中分析的数据，并在列表（“数据管理”类型工作流）或多维数据集（使用Marketing Analytics）中预聚合这些数据。 它将以数据透视表或组列表的形式显示。

   如需详细信息，请参阅[此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. **分析报表**:Marketing Analytics支持直观的数据探索。

   如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。

>[!CAUTION]
>
>为便于显示和操作以及高效导出，报表不得包含超过1,000行。
