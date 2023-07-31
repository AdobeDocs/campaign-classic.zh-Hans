---
product: campaign
title: 关于多维数据集
description: 多维数据集入门
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 3%

---

# 多维数据集入门{#about-cubes}



## 术语 {#terminology}

处理多维数据集时的具体术语如下所示。

* **多维数据集**  — 多维数据集是多维信息的表示形式：它向最终用户提供为交互式数据分析而设计的结构。

* **事实表/模式**  — 事实表（或事实模式）包含分析所依据的原始数据或基本数据。 这些表格主要是大型卷表（可能包含链接表），其计算时间可能会很长。 例如，事实表可以是：broadlog表、purchase表等。

* **Dimension**  — 通过Dimension，可将数据分组到组中：创建维后，维即用作分析轴。 在大多数情况下，将为给定维度定义多个级别。 例如，对于临时维度，级别将为月、日、小时、分钟等。 这组级别表示维层次结构并启用各种级别的数据分析。

* **量化**  — 对于某些字段，您可以定义对值进行分组，使其更易于阅读信息。 量化应用于级别。 我们建议您在可能有许多不同值时定义量化。

* **衡量**  — 最常见的度量是总和、平均值、最大值、最小值、标准偏差等。 可以计算度量：例如，优惠的接受率是提供该优惠的次数与接受该优惠的次数之比。

## 多维数据集工作区 {#cube-workspace}

多维数据集存储在 **[!UICONTROL Administration > Configuration > Cubes]** 节点。

![](assets/s_advuser_cube_node.png)

多维数据集的主要使用上下文如下：

* 数据导出可以直接在报表中执行，报表设计于 **[!UICONTROL Reports]** Adobe Campaign选项卡。

  要执行此操作，请创建新报告并选择要使用的多维数据集。

  ![](assets/cube_create_new.png)

  多维数据集看起来像模板，其创建基于哪些报告。 选择模板后，单击 **[!UICONTROL Create]** 以配置和查看匹配报表。

  您可以调整度量、更改显示模式或配置表，然后使用主按钮显示报表。

  ![](assets/cube_display_new.png)

* 您还可以在 **[!UICONTROL Query]** 框以使用指标，如下所示：

  ![](assets/s_advuser_query_using_a_cube.png)

* 您还可以将基于多维数据集的透视表插入报表的任何页面。 要执行此操作，请引用要用于 **[!UICONTROL Data]** 页上的数据透视表选项卡。

  ![](assets/s_advuser_cube_in_report.png)

  有关详细信息，请参见 [在报表中浏览数据](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
