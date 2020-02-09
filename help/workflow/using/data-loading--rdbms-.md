---
title: 数据加载(RDBMS)
seo-title: 数据加载(RDBMS)
description: 数据加载(RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 数据加载(RDBMS){#data-loading-rdbms}

通过 **[!UICONTROL Data loading (RDBMS)]** 该活动，您可以直接访问此外部数据库并仅收集定位所需的数据。

为了提高性能，我们建议使用查询活动（其中可以使用外部数据库的数据）。 有关详细信息，请参阅 [访问外部数据库(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

操作如下：

1. 从列表中选择数据源，然后输入包含要提取的数据的表的名称。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相应字段中输入的表的名称用作外部数据库中收集数据的模板。 通过数据加载活动的入站过渡可以计算或传送由工作流处理的表的名称。 要选择要使用的表，请单击 **[!UICONTROL Advanced..]**。 链接并选择 **[!UICONTROL Specified in the transition]** 或选 **[!UICONTROL Explicit]** 项。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 单击链 **[!UICONTROL Select the columns to extract...]** 接以选择要在数据库中收集的数据。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以为此数据定义过滤器。 要执行此操作，请单击链 **[!UICONTROL Edit query....]** 接。

   这样收集的数据可以在整个工作流的生命周期中使用。

