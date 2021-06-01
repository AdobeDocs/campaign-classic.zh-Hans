---
product: campaign
title: 关于多维数据集
description: 关于多维数据集
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 10%

---

# 多维数据集入门{#about-cubes}

通过&#x200B;**Marketing Analytics**&#x200B;模块，可探索数据库中的数据。 它使您能够分析和测量数据、计算统计数据、简化和优化报表的创建和计算。 除此之外，营销分析还允许您创建报表和构建目标群体。 识别后，这些区段会存储在可在Adobe Campaign中使用的列表（定位、分段等）中。

多维数据集用于生成某些内置报告，包括投放报告（投放跟踪、点击、打开等）。 基于多维数据集的报告只能用作500万条事实线以下数据卷的标准。

您可以扩展数据库探索和分析能力，同时使最终用户更容易配置报告和表：他们只需在创建其报告或表时选择现有（已经过完全配置）多维数据集，以处理计算、度量和统计。

创建和配置多维数据集后，报告查询框和 Web 应用程序中即会使用这些多维数据集。它们可以在数据透视表中使用和操作。

>[!CAUTION]
>
>**Marketing** Analytics和Adobe Campaign模块。需要在您的实例上安装它，以便您能够使用下面描述的功能。

借助Marketing Analytics模块，Campaign使您能够：

1. 在以下视图中创建多维数据集：

   * 将数据汇总并存储到工作表中，以根据用户需求预计指标，
   * 减少用于报告和查询的各种计算中涉及的数据量，从而显着优化指标计算时间，
   * 简化对数据的访问，使用户能够根据各种维度处理数据（无论是否预先聚合）。

   有关更多信息，请参阅[创建指示器](../../reporting/using/creating-indicators.md)。

1. 在以下视图中创建数据透视表：

   * 浏览计算数据，配置度量，
   * 选择要显示的数据及其显示模式，
   * 使用的措施和指标个性化，
   * 为具有非技术背景的用户提供交互式分析工具。

   有关更多信息，请参阅[使用多维数据集浏览数据](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用多维数据集中计算和聚合的数据构建查询。
1. 确定群体并在列表中引用它们。

## 术语 {#terminology}

使用多维数据集时，必须知道以下概念：

* 多维数据集

   立方体是多维信息的表示形式：它为最终用户提供了专为交互式数据分析而设计的结构。

* 事实表/模式

   事实表（或事实模式）包含分析所依据的原始或基本数据。 这些表主要是大容量表（可能包含链接表），其计算可能较长。

   例如，事实表可以是：broadlog表、purchase表等

* Dimension

   Dimension允许您将数据分段到以下组：创建维度后，这些维度将用作分析轴。 在大多数情况下，对于给定的维度，将定义多个级别。 例如，对于临时维度，级别将为月、天、小时、分钟等。 这组级别表示维度层次结构，并支持各种级别的数据分析。

* 宾宁

   对于某些字段，您可以定义绑定到组值，并更便于读取信息。 绑定应用于级别

   我们建议您在可能存在许多不同值时定义绑定。

* 测量

   最常用的度量是和、平均、最大、最小、标准差等。

   可以计算度量：例如，要约的接受率是其被呈现的次数与被接受次数的比率。

## 多维数据集工作区{#cube-workspace}

多维数据集存储在&#x200B;**[!UICONTROL Administration > Configuration > Cubes]**&#x200B;节点中。

![](assets/s_advuser_cube_node.png)

多维数据集使用的主要上下文如下：

* 数据导出可以直接在Adobe Campaign平台&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡中设计的报表中执行。

   要实现此目的，请创建新报告并选择要使用的多维数据集。

   ![](assets/cube_create_new.png)

   多维数据集的显示方式与创建报告时所依据的模板类似。 选择模板后，单击&#x200B;**[!UICONTROL Create]**&#x200B;以配置和查看匹配的报表。

   您可以调整测量、更改显示模式或配置表格，然后使用主按钮显示报表。

   ![](assets/cube_display_new.png)

* 您还可以引用报表&#x200B;**[!UICONTROL Query]**&#x200B;框中的多维数据集以使用其指示器，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您还可以将基于多维数据集的数据透视表插入报表的任何页面。 要实现此目的，请引用要在相关页面上数据透视表的&#x200B;**[!UICONTROL Data]**&#x200B;选项卡中使用的多维数据集。

   ![](assets/s_advuser_cube_in_report.png)

   有关更多信息，请参阅[探索报表中的数据](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)。
