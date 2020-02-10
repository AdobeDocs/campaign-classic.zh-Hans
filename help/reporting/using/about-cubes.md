---
title: 关于立方
seo-title: 关于立方
description: 关于立方
seo-description: null
page-status-flag: never-activated
uuid: 429bd5e9-288a-4c71-9b01-c4c5690f5abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 42db3be8-ee02-4158-adcd-846420a32460
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 关于立方{#about-cubes}

通过 **Marketing Analytics模块提供对数据库中数据的探** 索。 它使您能够分析和测量数据、计算统计数据、简化和优化报表创建和计算。 除此之外，Marketing Analytics还允许您创建报告和构建目标人群。 一旦识别了这些内容，它们就会存储在可用于Adobe Campaign（定位、细分等）的列表中。

多维数据集用于生成某些内置报表，包括交付报表（交付跟踪、点击、打开等）。 基于立方的报告只能用作500万条数据线以下的数据卷的标准。

您可以扩展数据库探索和分析能力，同时让最终用户更轻松地配置报告和表：他们只需在创建其报表或表时选择一个现有（完全配置的）立方体即可处理计算、度量和统计信息。

创建和配置多维数据集后，将在报表查询框和Web应用程序中使用它们。 它们可以在枢纽表内使用和操作。

>[!CAUTION]
>
>**Marketing Analytics是Adobe** Campaign的一个模块。 它需要安装在实例上，这样您就可以使用下面描述的功能。

利用Marketing Analytics模块，Campaign使您能够：

1. 在以下视图中创建立方：

   * 将数据汇总并存储在工作表中，以根据用户需求预计指标，
   * 减少了用于报告和查询的各种计算中涉及的数据量，从而显着优化了指标计算时间，
   * 简化对数据的访问，使用户能够根据各种维度操作数据（无论是否预聚集）。
   For more on this, refer to [Creating indicators](../../reporting/using/creating-indicators.md).

1. 在以下视图中创建透视表：

   * 探索计算数据，配置度量，
   * 选择要显示的数据及其显示模式，
   * 使用的措施和指标个性化，
   * 为具有非技术背景的用户提供交互式分析工具。
   有关此功能的详细信息，请参 [阅使用多维数据集探索数据](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用在立方中计算和聚集的数据构建查询。
1. 确定人群并在列表中引用它们。

## 术语 {#terminology}

使用立方时，必须知道以下概念：

* 立方体

   立方体是多维信息的表示形式：它为最终用户提供了为交互式数据分析而设计的结构。

* 事实表／架构

   事实表（或事实架构）包含分析所基于的原始或基本数据。 这些表主要是具有可能较长计算的大容量表（可能包含链接表）。

   例如，事实表可以是：广播表、购买表等。

* Dimension

   维允许您将数据细分到组中：创建维后，这些维用作分析轴。 在大多数情况下，对于给定维，将定义多个级别。 例如，对于时间维度，级别将为月、天、小时、分钟等。 这组级别表示维层次结构，并支持不同级别的数据分析。

* Binning

   对于某些字段，您可以定义绑定以组值，并使其更容易读取信息。 绑定应用于级别

   我们建议您在可能存在许多不同值时定义绑定。

* 测量

   最频繁的测量方法有求和、平均、最大值、最小值、标准差等。

   可以计算度量：例如，要约的接受率是其被提出的次数与被接受的次数之比。

## 立方工作区 {#cube-workspace}

多维数据集存储在节 **[!UICONTROL Administration > Configuration > Cubes]** 点中。

![](assets/s_advuser_cube_node.png)

立方的主要使用上下文如下：

* 数据导出可以直接在Adobe Campaign平台范围内设计的报 **[!UICONTROL Reports]** 告中执行。

   为此，请创建新报表并选择要使用的多维数据集。

   ![](assets/cube_create_new.png)

   多维数据集的显示方式与创建报表时所使用的模板类似。 选择模板后，单击以配 **[!UICONTROL Create]** 置和查看匹配的报告。

   您可以调整度量、更改显示模式或配置表，然后使用主按钮显示报告。

   ![](assets/cube_display_new.png)

* 您还可以引用报表框中的 **[!UICONTROL Query]** 立方体来使用其指示器，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您还可以将基于立方的透视表插入报表的任何页面。 为此，请引用要在相关页面的透视表 **[!UICONTROL Data]** 选项卡中使用的立方。

   ![](assets/s_advuser_cube_in_report.png)

   有关此问题的详细信息，请参 [阅探索报告中的数据](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)。

