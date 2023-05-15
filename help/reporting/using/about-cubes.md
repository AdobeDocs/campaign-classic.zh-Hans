---
product: campaign
title: 关于多维数据集
description: 多维数据集入门
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# 多维数据集入门{#about-cubes}



## 术语 {#terminology}

下面列出了处理多维数据集时的特定术语。

* **多维数据集**  — 多维数据集是多维信息的表示：它为最终用户提供了专为交互式数据分析而设计的结构。

* **事实表/模式**  — 事实表（或事实模式）包含分析所依据的原始或基本数据。 这些表主要是大容量表（可能包含链接表），其计算可能较长。 例如，事实表可以是：broadlog表、purchase表等

* **Dimension** -Dimension允许您将数据分段为组：创建维度后，这些维度将用作分析轴。 在大多数情况下，对于给定的维度，将定义多个级别。 例如，对于临时维度，级别将为月、天、小时、分钟等。 这组级别表示维度层次结构，并支持各种级别的数据分析。

* **宾宁**  — 对于某些字段，您可以定义绑定到组值，并更便于读取信息。 绑定应用于级别。 我们建议您在可能存在许多不同值时定义绑定。

* **测量**  — 最频繁的措施是求和、平均、最大、最小、标准偏差等。 可以计算度量：例如，要约的接受率是其被呈现次数与被接受次数之比。

## 立方工作区 {#cube-workspace}

多维数据集存储在 **[!UICONTROL Administration > Configuration > Cubes]** 节点。

![](assets/s_advuser_cube_node.png)

多维数据集使用的主要上下文如下：

* 数据导出可以直接在报表中执行，该报表在 **[!UICONTROL Reports]** 选项卡。

   要实现此目的，请创建新报告并选择要使用的多维数据集。

   ![](assets/cube_create_new.png)

   多维数据集的显示方式与创建报告时所依据的模板类似。 选择模板后，单击 **[!UICONTROL Create]** 配置和查看匹配报表。

   您可以调整测量、更改显示模式或配置表格，然后使用主按钮显示报表。

   ![](assets/cube_display_new.png)

* 您还可以在 **[!UICONTROL Query]** 报表框以使用其指标，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您还可以将基于多维数据集的数据透视表插入报表的任何页面。 为此，请引用 **[!UICONTROL Data]** 选项卡。

   ![](assets/s_advuser_cube_in_report.png)

   有关更多信息，请参阅 [浏览报表中的数据](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
