---
solution: Campaign Classic
product: campaign
title: 更改维度
description: 更改维度
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# 更改维度{#change-dimension}

更改维度活动允许您在目标构建周期中更改定位维度。 轴偏移取决于数据模板和输入维度。 这允许您从“合同”维切换到“客户”维，例如。

您还可以使用此活动定义新目标的附加列。

可以定义数据外部重复数据删除条件。

## 配置模式{#configuration-mode}

要配置更改维度活动，请应用以下步骤：

1. 通过&#x200B;**[!UICONTROL Change dimension]**&#x200B;字段选择新定位维度。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸更改期间，您可以保留所有元素或选择要保留在输出中的元素。 在以下示例中，max。 重复数设置为2。

   ![](assets/s_user_change_dimension_limit.png)

   当您选择仅保留一条记录时，将在工作模式中显示一个集合：此集合表示在最终结果中不会定位的所有记录（因为只保留一条记录）。 与所有其他集合一样，此集合允许您计算聚合或恢复列中的信息。

   例如，如果将&#x200B;**[!UICONTROL Customers]**&#x200B;维度更改为&#x200B;**[!UICONTROL Recipients]**&#x200B;维度，则可以在添加购买次数的同时目标特定商店的客户。

1. 如果选择不保留所有这些信息，则可以配置重复管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   蓝色箭头允许您定义重复处理优先级。

   在上例中，收件人将首先在其电子邮件地址上删除重复项，然后在必要时在其帐户号上删除重复项。

1. **[!UICONTROL Result]**&#x200B;选项卡允许您添加其他信息。

   例如，您可以使用&#x200B;**子字符串**&#x200B;类型函数根据邮政编码恢复县。 操作步骤：

   * 单击&#x200B;**[!UICONTROL Add data...]**&#x200B;链接并选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**。

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >有关创建和管理其他列的信息，请参阅[添加数据](../../workflow/using/query.md#adding-data)。

   * 选择上一个定位维度（在轴切换之前），在收件人的&#x200B;**[!UICONTROL Location]**&#x200B;子树中选择&#x200B;**[!UICONTROL Zip Code]**，然后单击&#x200B;**[!UICONTROL Edit expression]**。

      ![](assets/wf_change-dimension_sample_02.png)

   * 单击&#x200B;**[!UICONTROL Advanced selection]**，然后选择&#x200B;**[!UICONTROL Edit the formula using an expression]**。

      ![](assets/wf_change-dimension_sample_03.png)

   * 使用列表中提供的函数并指定要执行的计算。

      ![](assets/wf_change-dimension_sample_04.png)

   * 最后，输入刚刚创建的列的标签。

      ![](assets/wf_change-dimension_sample_05.png)

1. 执行工作流以视图此配置的结果。 比较更改维度活动前后表中的数据，并比较工作流表的结构，如下例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

