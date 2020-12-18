---
solution: Campaign Classic
product: campaign
title: 关于Adobe Campaign报告工具
description: 在内建或自定义报告中，分析促销活动成功与否。
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 16%

---


# 开始使用报告 {#about-adobe-campaign-reporting-tools}

除了[内置报告](../../reporting/using/about-campaign-built-in-reports.md)之外，Adobe Campaign还允许您在各种上下文中生成报告并满足不同的需求。 本文档详细介绍了使用原则和实施模式。

Adobe Campaign不是专门的报告工具：在Adobe Campaign中创建的报告主要允许您视图聚合数据。 Adobe Campaign报告专门用于分析和表示数据，但并非为数据库导出而设计。

要从Adobe Campaign库导出数据，您需要创建工作流并使用数据导出活动。 如需详细信息，请参阅[此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供多种报告工具：

1. **内置报告**:Adobe Campaign优惠投放、活动、平台活动、可选功能等的一组报告。这些报告可通过其相关的各种功能获得。 它们可以适应您的特定需求。

   如需详细信息，请参阅[此部分](../../reporting/using/about-campaign-built-in-reports.md)。

1. **描述性数据分析**:Adobe Campaign提供了一个可视化工具，用于生成有关数据库中数据的统计信息。您可以使用专用向导创建描述性分析报告，并根据需要调整其内容和布局。

   如需详细信息，请参阅[此部分](../../reporting/using/about-descriptive-analysis.md)。

1. **个性化报告**:Adobe Campaign允许您创建有关数据库中数据的报告。创建这些组件后，即可在相应的上下文中访问它们。

   根据查询、计算和卷的复杂性，这些报告中分析的数据可以通过查询收集，并在列表(“数据管理”类型工作流)或多维数据集（使用营销分析）中预先聚集。 它将以透视表或组列表的形式显示。

   如需详细信息，请参阅[此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. **分析报告**:营销分析可以实现直观的数据探索。

   如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。

>[!CAUTION]
>
>为了便于显示和操作，以及高效导出，报表必须包含1,000行以上。