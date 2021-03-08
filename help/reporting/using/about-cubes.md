---
solution: Campaign Classic
product: campaign
title: 关于多维数据集
description: 关于多维数据集
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 10%

---


# 开始使用多维数据集{#about-cubes}

通过&#x200B;**营销分析**&#x200B;模块提供对数据库中数据的探索。 它使您能够分析和测量数据、计算统计、简化和优化报表创建和计算。 除此之外，Marketing Analytics还允许您创建报告和构建目标群。 一旦识别出这些内容，它们就会存储在可用于Adobe Campaign（定位、分段等）的列表中。

多维数据集用于生成某些内置报表，包括投放报告(投放跟踪、点击、打开等)。 基于多维数据集的报告只能用作500万条事实线以下数据量的标准。

您可以扩展数据库探索和分析能力，同时使最终用户更容易配置报告和表：他们只需在创建其报告或表时选择现有（已经过完全配置）多维数据集，以处理计算、度量和统计。

创建和配置多维数据集后，报告查询框和 Web 应用程序中即会使用这些多维数据集。它们可以在数据透视表中使用和操作。

>[!CAUTION]
>
>**营销** 分析是Adobe Campaign模块。它需要安装在您的实例中，以便您可以使用下面描述的功能。

利用营销分析模块，活动使您能够：

1. 创建多维数据集视图:

   * 将数据汇总并存储在工作表中，根据用户需求预计指标，
   * 减少用于报告和查询的各种计算中涉及的数据量，从而显着优化指标计算时间，
   * 简化对数据的访问，使用户能够根据各种维度操作数据（无论是否预聚集）。

   有关详细信息，请参阅[创建指示器](../../reporting/using/creating-indicators.md)。

1. 在以下视图创建透视表：

   * 探索计算数据，配置度量，
   * 选择要显示的数据及其显示模式，
   * 使用的措施和指标个性化，
   * 为具有非技术背景的用户提供交互式分析工具。

   有关详细信息，请参阅[使用多维数据集浏览数据](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用在查询中计算和聚集的数据构建多维数据集。
1. 确定人群并在列表中引用。

## 术语 {#terminology}

使用多维数据集时，必须知道以下概念：

* 多维数据集

   多维数据集是多维信息的表示：它为最终用户提供了专为交互式数据分析而设计的结构。

* 数值表/模式

   事实表(或事实模式)包含分析所依据的原始或基本数据。 这些表主要是具有可能较长计算的大卷表（可能包含链接表）。

   例如，事实表可以是：broadlog表、购买表等。

* Dimension

   Dimension允许您将数据细分为组：创建这些尺寸后，这些尺寸将用作分析轴。 在大多数情况下，对于给定的维度，将定义多个级别。 例如，对于时间维度，级别将为月、天、小时、分钟等。 这组级别表示维层次，并启用不同级别的数据分析。

* Binning

   对于某些字段，您可以定义绑定以组值，并使其更容易读取信息。 绑定应用于级别

   我们建议您在可能有多个不同值时定义绑定。

* 度量

   最频繁的措施是求和、平均、最大值、最小值、标准偏差等。

   可以计算度量：例如，优惠的接受率是其被呈现的次数与被接受的次数之比。

## 多维数据集工作区{#cube-workspace}

多维数据集存储在&#x200B;**[!UICONTROL Administration > Configuration > Cubes]**&#x200B;节点中。

![](assets/s_advuser_cube_node.png)

多维数据集的主要上下文如下：

* 数据导出可以直接在Adobe Campaign平台的&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡中设计的报告中执行。

   为此，请创建新报表并选择要使用的多维数据集。

   ![](assets/cube_create_new.png)

   多维数据集的显示方式与创建报表的模板类似。 选择模板后，单击&#x200B;**[!UICONTROL Create]**&#x200B;配置并视图匹配报表。

   您可以调整度量、更改显示模式或配置表，然后使用主按钮显示报表。

   ![](assets/cube_display_new.png)

* 您还可以引用报表&#x200B;**[!UICONTROL Query]**&#x200B;框中的多维数据集来使用其指示器，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您还可以将基于多维数据集的透视表插入报表的任何页面。 为此，请引用要在相关页面上的数据透视表&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中使用的多维数据集。

   ![](assets/s_advuser_cube_in_report.png)

   有关详细信息，请参阅[探索报表](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)中的数据。

