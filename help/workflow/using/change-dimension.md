---
product: campaign
title: 更改维度
description: 更改维度
feature: Workflows, Targeting Activity
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---

# 更改维度{#change-dimension}



通过更改维度活动，可在目标构建周期中更改定向维度。 轴偏移取决于数据模板和输入维度。 例如，您可以从“合同”维度切换到“客户”维度。

您还可以使用此活动来定义新目标的附加列。

可以定义重复数据删除标准。

## 配置模式 {#configuration-mode}

要配置更改维活动，请应用以下步骤：

1. 通过选择新的定向维度 **[!UICONTROL Change dimension]** 字段。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸更改过程中，可保留所有元素或选取要保留在输出中的元素。 在以下示例中，最大 重复项数设置为2。

   ![](assets/s_user_change_dimension_limit.png)

   当您选择只保留一个记录时，会在工作架构中显示一个集合：此集合表示在最终结果中不会定向的所有记录（因为只保留一个记录）。 与所有其他收藏集一样，这个收藏集允许您计算聚合或恢复列中的信息。

   例如，如果更改 **[!UICONTROL Customers]** 维到 **[!UICONTROL Recipients]** 维度时，可以定位特定商店的客户，同时添加已购买的次数。

1. 如果选择不保留所有这些信息，则可以配置复制管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   蓝色箭头允许您定义重复的处理优先级。

   在上面的示例中，将先在收件人的电子邮件地址上删除重复项，然后根据需要在其帐号上删除重复项。

1. 此 **[!UICONTROL Result]** 选项卡可让您添加其他信息。

   例如，您可以使用根据邮政编码恢复县 **子字符串** type函数。 操作步骤：

   * 单击 **[!UICONTROL Add data...]** 链接并选择 **[!UICONTROL Data linked to the filtering dimension]**.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >有关创建和管理其他列的信息，请参阅 [添加数据](query.md#adding-data).

   * 选择上一个定向尺寸（在轴切换前），然后选择 **[!UICONTROL Zip Code]** 在收件人的 **[!UICONTROL Location]** 子树，然后单击 **[!UICONTROL Edit expression]**.

     ![](assets/wf_change-dimension_sample_02.png)

   * 单击 **[!UICONTROL Advanced selection]** 并选择 **[!UICONTROL Edit the formula using an expression]**.

     ![](assets/wf_change-dimension_sample_03.png)

   * 使用列表中提供的函数并指定要执行的计算。

     ![](assets/wf_change-dimension_sample_04.png)

   * 最后，输入刚刚创建的列的标签。

     ![](assets/wf_change-dimension_sample_05.png)

1. 执行工作流可查看此配置的结果。 比较变更维活动之前和之后的表中的数据，并比较工作流表的结构，如以下示例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
