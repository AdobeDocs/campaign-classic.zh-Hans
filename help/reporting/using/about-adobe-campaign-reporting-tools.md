---
title: 关于Adobe Campaign报告工具
seo-title: 关于Adobe Campaign报告工具
description: 关于Adobe Campaign报告工具
seo-description: null
page-status-flag: never-activated
uuid: a8122c9e-60ba-4ef7-bc63-05d6cf16fad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: c5dad561-0708-4b7a-84a0-eb00beff58c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1719d6ac9643f0b3e9339037cf4d0f209d16340e

---


# 报告入门 {#about-adobe-campaign-reporting-tools}

In addition to [built-in reports](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign lets you generate reports in various contexts and to meet different needs. 本文详细介绍了使用原则和实施模式。

Adobe Campaign不是专门的报告工具：在Adobe Campaign中创建的报告主要允许您查看汇总的数据。 专门用于分析和表示数据的Adobe Campaign报告并非为数据库导出而设计。

要从Adobe Campaign数据库导出数据，您需要创建工作流并使用数据导出活动。 如需详细信息，请参阅[此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供多种报告工具：

1. **内置报告**:Adobe Campaign提供了一组有关交付、营销活动、平台活动、可选功能等的报告。 这些报告可通过其相关的各种功能获得。 它们可以根据您的特定需求进行调整。

   如需详细信息，请参阅[此部分](../../reporting/using/about-campaign-built-in-reports.md)。

1. **描述性数据分析**:Adobe Campaign提供了一个可视化工具，用于生成有关数据库中数据的统计信息。 您可以使用专用向导创建描述性分析报告，并根据需要调整其内容和布局。

   如需详细信息，请参阅[此部分](../../reporting/using/about-descriptive-analysis.md)。

1. **个性化报告**:Adobe Campaign允许您创建有关数据库中数据的报告。 创建这些组件后，它们便可在相应的上下文中访问。

   根据查询、计算和卷的复杂性，这些报告中分析的数据可以通过查询收集并预先聚集到列表（“数据管理”类型工作流）或立方（使用Marketing Analytics）中。 它将以透视表或组列表的形式显示。

   如需详细信息，请参阅[此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. **分析报告**:营销分析支持直观的数据探索。

   如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。

>[!CAUTION]
>
>为了便于显示和操作，以及高效导出，报表中不得包含超过1,000行。