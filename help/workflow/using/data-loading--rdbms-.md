---
product: campaign
title: 数据加载 (RDBMS)
description: 了解有关数据加载(RDBMS)工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# 数据加载 (RDBMS){#data-loading-rdbms}



的 **[!UICONTROL Data loading (RDBMS)]** 活动允许您直接访问此外部数据库，并仅收集定位所需的数据。

为了提高性能，我们建议使用查询活动（可在其中使用外部数据库的数据）。 有关更多信息，请参阅 [访问外部数据库(FDA)](accessing-an-external-database--fda-.md).

操作如下：

1. 从列表中选择数据源，然后输入包含要提取的数据的表的名称。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相应字段中输入的表名称将用作外部数据库中收集数据的模板。 通过数据加载活动的集客过渡，可以计算或传递由工作流处理的表的名称。 要选择要使用的表，请单击 **[!UICONTROL Advanced..]**. 链接并选择 **[!UICONTROL Specified in the transition]** 或 **[!UICONTROL Explicit]** 选项。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 单击 **[!UICONTROL Select the columns to extract...]** 链接以选择要在数据库中收集的数据。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以根据此数据定义过滤器。 为此，请单击 **[!UICONTROL Edit query....]** 链接。

   像这样收集的数据可以在工作流的整个生命周期中使用。
