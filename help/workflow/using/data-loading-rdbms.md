---
product: campaign
title: 数据加载 (RDBMS)
description: 了解有关数据加载(RDBMS)工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 6%

---

# 数据加载 (RDBMS){#data-loading-rdbms}



此 **[!UICONTROL Data loading (RDBMS)]** 通过活动，您可以直接访问此外部数据库，并仅收集定位所需的数据。

为了提高性能，我们建议使用查询活动（可在其中使用外部数据库的数据）。 有关详细信息，请参见 [访问外部数据库（联合数据访问）](accessing-an-external-database-fda.md).

操作如下：

1. 从列表中选择数据源，然后输入包含要提取的数据的表的名称。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相应字段中输入的表的名称将用作在外部数据库中收集数据的模板。 工作流处理的表的名称可以由数据加载活动的集客过渡计算或传递。 要选择要使用的表，请单击 **[!UICONTROL Advanced..]**. 链接并选择 **[!UICONTROL Specified in the transition]** 或 **[!UICONTROL Explicit]** 选项。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 单击 **[!UICONTROL Select the columns to extract...]** 用于选择要从数据库中收集的数据的链接。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以根据此数据定义过滤器。 要执行此操作，请单击 **[!UICONTROL Edit query....]** 链接。

   这样收集的数据可在工作流的整个生命周期中使用。
