---
title: 更改维度
seo-title: 更改维度
description: 更改维度
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 2%

---


# 更改维度{#change-dimension}

更改维度活动允许您在目标构建周期中更改定位维度。 轴偏移取决于数据模板和输入维。 这允许您从“合同”维切换到“客户端”维，例如。

您还可以使用此活动定义新目标的附加列。

可以定义数据外部重复数据删除标准。

## 配置模式 {#configuration-mode}

要配置更改维度活动，请应用以下步骤：

1. 通过字段选择新定位维度 **[!UICONTROL Change dimension]** 符。

   ![](assets/s_user_change_dimension_param1.png)

1. 在尺寸更改过程中，您可以保留所有元素或选择要保留在输出中的元素。 在以下示例中，最大值。 重复数设置为2。

   ![](assets/s_user_change_dimension_limit.png)

   当您选择只保留一条记录时，集合会显示在工作模式中：此集合表示在最终结果中不会定位的所有记录（因为只保留一个记录）。 与所有其他集合一样，此集合允许您计算聚合或恢复列中的信息。

   例如，如果将维 **[!UICONTROL Customers]** 度更改为 **[!UICONTROL Recipients]** 维度，则可以在添加购买次数时目标特定商店的客户。

1. 如果选择不保留所有这些信息，则可以配置重复管理模式。

   ![](assets/s_user_change_dimension_param2.png)

   蓝色箭头允许您定义重复处理优先级。

   在上例中，收件人将首先在其电子邮件地址上进行重复数据消除，然后根据需要在其帐户号码上进行消除重复。

1. 在该 **[!UICONTROL Result]** 选项卡中可添加其他信息。

   例如，您可以使用子字符串类型函数根据邮政编码恢 **复县** 。 操作步骤：

   * 单击链 **[!UICONTROL Add data...]** 接并选择 **[!UICONTROL Data linked to the filtering dimension]**。

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >有关创建和管理其他列的信息，请参阅添 [加数据](../../workflow/using/query.md#adding-data)。

   * 选择上一个定位维度（在轴切换之前），在 **[!UICONTROL Zip Code]** 收件人的子树中 **[!UICONTROL Location]** 选择该，然后单击 **[!UICONTROL Edit expression]**。

      ![](assets/wf_change-dimension_sample_02.png)

   * 单击 **[!UICONTROL Advanced selection]** 并选择 **[!UICONTROL Edit the formula using an expression]**。

      ![](assets/wf_change-dimension_sample_03.png)

   * 使用列表中提供的函数并指定要执行的计算。

      ![](assets/wf_change-dimension_sample_04.png)

   * 最后，输入刚刚创建的列的标签。

      ![](assets/wf_change-dimension_sample_05.png)

1. 执行工作流以视图此配置的结果。 比较更改维度活动前后表中的数据，并比较工作流表的结构，如以下示例所示：

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

