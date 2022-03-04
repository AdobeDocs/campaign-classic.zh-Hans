---
product: campaign
title: 投放概要
description: 了解有关投放大纲工作流活动的更多信息
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 投放概要{#delivery-outline}

![](../../assets/common.svg)

的 **投放概要** 可让您在营销活动工作流中使用大纲。 必须事先在营销活动中创建大纲。

有关Adobe Campaign中投放大纲的更多信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

要配置活动，您只需选择所需的大纲以及计划的联系日期即可。 您可以通过添加分类或分类规则来添加筛选规则。

## 示例：通过投放大纲插入选件 {#example--inserting-an-offer-via-a-delivery-outline}

的 **投放概要** 活动（在营销活动工作流中提供）允许您显示在当前正在进行的营销活动的投放大纲中引用的选件。

>[!NOTE]
>
>的 **互动** 必须安装包。

1. 在工作流中，添加投放大纲活动后再添加投放活动。
1. 在投放大纲活动中，指定要使用的大纲。

   有关指定投放大纲的更多信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. 根据您的投放填写可用字段。
1. 可能有两种情况：

   * 如果要调用选件引擎，请检查 **[!UICONTROL Restrict the number of propositions selected]** 框中。 指定优惠空间以及将在投放中呈现的建议数。

      选件引擎将考虑选件权重和资格规则。

   * 如果不勾选方框，则无需调用选件引擎即会显示投放大纲中的所有选件。

   预览会考虑投放中指定的选件数量。 执行工作流时，它是在投放大纲中指定的要考虑的编号。

   ![](assets/int_compo_offre_wf1.png)
