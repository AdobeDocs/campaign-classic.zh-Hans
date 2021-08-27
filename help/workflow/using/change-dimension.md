---
product: campaign
title: 更改维度
description: 更改维度
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# 更改维度{#change-dimension}

![](../../assets/common.svg)

通过更改维度活动，您可以在目标构建周期中更改定向维度。 轴移动取决于数据模板和输入维度。 例如，您可以从“合同”维度切换到“客户”维度。

您还可以使用此活动来定义新目标的其他列。

可以定义重复数据删除标准。

## 配置模式 {#configuration-mode}

要配置更改维度活动，请应用以下步骤：

1. 通过&#x200B;**[!UICONTROL Change dimension]**&#x200B;字段选择新的定向维度。

   ![](assets/s_user_change_dimension_param1.png)

1. 在维度更改期间，您可以保留所有元素或选择要保留在输出中的元素。 在以下示例中，为max。 重复项数量设置为2。

   ![](assets/s_user_change_dimension_limit.png)

   如果选择仅保留一条记录，则工作架构中会显示一个集合：此集合表示在最终结果中不会定向的所有记录（因为只保留一个记录）。 与所有其他集合一样，此集合允许您计算聚合或恢复列中的信息。

   例如，如果将&#x200B;**[!UICONTROL Customers]**&#x200B;维度更改为&#x200B;**[!UICONTROL Recipients]**&#x200B;维度，则可以在添加购买次数的同时定位特定商店的客户。

1. 如果选择不保留所有这些信息，则可以配置复制管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   蓝色箭头允许您定义重复的处理优先级。

   在以上示例中，收件人首先会在其电子邮件地址上删除重复项，然后根据需要在其帐号上删除重复项。

1. 使用&#x200B;**[!UICONTROL Result]**&#x200B;选项卡可添加其他信息。

   例如，您可以使用&#x200B;**Substring**&#x200B;类型函数根据邮政编码恢复县。 操作步骤：

   * 单击&#x200B;**[!UICONTROL Add data...]**&#x200B;链接并选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**。

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >有关创建和管理其他列的信息，请参阅[添加数据](query.md#adding-data)。

   * 选择前一个定向维度（在轴切换之前），在收件人的&#x200B;**[!UICONTROL Location]**&#x200B;子树中选择&#x200B;**[!UICONTROL Zip Code]**，然后单击&#x200B;**[!UICONTROL Edit expression]**。

      ![](assets/wf_change-dimension_sample_02.png)

   * 单击&#x200B;**[!UICONTROL Advanced selection]**&#x200B;并选择&#x200B;**[!UICONTROL Edit the formula using an expression]**。

      ![](assets/wf_change-dimension_sample_03.png)

   * 使用列表中提供的函数并指定要执行的计算。

      ![](assets/wf_change-dimension_sample_04.png)

   * 最后，输入刚刚创建的列的标签。

      ![](assets/wf_change-dimension_sample_05.png)

1. 执行工作流以查看此配置的结果。 比较更改维度活动前后表格中的数据，并比较工作流表的结构，如以下示例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
