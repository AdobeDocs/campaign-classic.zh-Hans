---
solution: Campaign Classic
product: campaign
title: 数据加载 (RDBMS)
description: 了解有关数据加载(RDBMS)工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---


# 数据加载 (RDBMS){#data-loading-rdbms}

**[!UICONTROL Data loading (RDBMS)]**&#x200B;活动允许您直接访问此外部数据库，并仅收集定位所需的数据。

为了提高性能，我们建议使用查询活动（可以使用外部数据库的数据）。 有关详细信息，请参阅[访问外部数据库(联合数据访问)](../../workflow/using/accessing-an-external-database--fda-.md)。

操作如下：

1. 从列表中选择数据源，并输入包含要提取数据的表的名称。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相应字段中输入的表的名称用作在外部数据库中收集数据的模板。 通过数据加载活动的入站过渡，可以计算或传送由工作流处理的表的名称。 要选择要使用的表，请单击&#x200B;**[!UICONTROL Advanced..]**。 链接并选择&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;或&#x200B;**[!UICONTROL Explicit]**&#x200B;选项。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 单击&#x200B;**[!UICONTROL Select the columns to extract...]**&#x200B;链接以选择要在数据库中收集的数据。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以定义此数据的过滤器。 为此，请单击&#x200B;**[!UICONTROL Edit query....]**&#x200B;链接。

   这样收集的数据可以在整个工作流的生命周期中使用。

