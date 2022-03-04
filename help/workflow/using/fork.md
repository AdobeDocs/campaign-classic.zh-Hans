---
product: campaign
title: 分叉
description: 进一步了解分支工作流活动
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 分叉{#fork}

![](../../assets/common.svg)

您可以使用 **[!UICONTROL Fork]** 活动创建多个叫客过渡，并在同一工作流中独立运行多个活动。

>[!IMPORTANT]
>
>您在 **[!UICONTROL Fork]** 活动不会同时运行。 此行为可能会影响工作流的性能。 使用 **[!UICONTROL Fork]** 活动。 或者，您也可以在工作流后续部分之前加入叫客活动。

配置 **[!UICONTROL Fork]** 活动及其相关活动，请按照以下步骤操作：

1. 打开 **[!UICONTROL Fork]** 活动，并定义叫客过渡的名称和标签。

   ![](assets/s_user_segmentation_fork.png)

1. 打开每个叫客过渡并对其进行配置。
1. （可选）要加入叫客过渡，请添加“与”加入活动。 [了解详情](and-join.md)。

   工作流的后续部分仅在连接的叫客过渡完成后才运行。

## 示例：分段

在此示例中，会向不同的群体组发送不同的电子邮件。 A **[!UICONTROL Fork]** 活动在查询后使用，以并行执行两个操作：

* 保存查询结果
* 对结果进行分段以发送多个投放

   ![分支活动遵循两个查询的交集，并在列表更新活动和拆分活动之前。](assets/wkf_fork_example.png)

工作流包含以下活动：

1. **[!UICONTROL Query]** 活动

   选择了两个群体组：女人和巴黎人。

1. **[!UICONTROL Intersection]** 活动

   选择查询结果的交集，即巴黎女人。

1. **[!UICONTROL Fork]** 活动

   计算的群体将被保存，并且会并行划分为两个组：

   1. 18至40岁的巴黎女性
   1. 40岁以上巴黎女性

1. **[!UICONTROL Delivery]** 活动

   会向每个群体组发送不同的电子邮件。

## 用例：发送生日电子邮件

会在收件人的生日当天向其列表发送定期电子邮件。 A **[!UICONTROL Fork]** 活动用于包含2月29日出生于闰年的收件人。 [了解更多](sending-a-birthday-email.md) 关于此用例。

![分支活动遵循测试活动，并位于两个查询活动之前。](assets/birthday-workflow_usecase_1.png)

## 用例：使用工作流自动化内容

内容块的创建和交付是自动的。 A **[!UICONTROL Fork]** 活动用于计算目标，并行用于创建内容。 [了解更多](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 关于此用例。

![分支活动跟在投放活动之后，位于查询活动和内容管理活动之前，二者均通过AND连接活动进行连接。](../../delivery/using/assets/d_ncs_content_workflow10.png)

然后，您可以配置每个叫客过渡，然后使用 [AND — 连接](and-join.md) 活动（如果需要）。 这样，工作流的其余部分将仅在 **[!UICONTROL Fork]** 活动的叫客过渡已完成。

## 相关主题

* [AND — 连接活动](and-join.md)
* [用例：生日电子邮件](sending-a-birthday-email.md)
* [用例：内容创建和交付](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)