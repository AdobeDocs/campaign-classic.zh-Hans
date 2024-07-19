---
product: campaign
title: 投放概要
description: 了解有关投放概要工作流活动的更多信息
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 投放概要{#delivery-outline}



**投放大纲**&#x200B;允许您在营销活动工作流中使用大纲。 必须预先在营销活动中创建大纲。

有关Adobe Campaign中投放概要的更多信息，请参阅此[部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活动，您只需选择喜欢的大纲以及计划的联系日期即可。 您可以通过添加分类或分类规则来添加筛选规则。

## 示例：通过投放概要插入选件 {#example--inserting-an-offer-via-a-delivery-outline}

营销活动工作流中可用的&#x200B;**投放概要**&#x200B;活动可让您提供在当前营销活动的投放概要中引用的优惠。

>[!NOTE]
>
>必须安装&#x200B;**交互**&#x200B;程序包。

1. 在工作流中，添加投放概要活动，然后再添加投放活动。
1. 在投放大纲活动中，指定要使用的大纲。

   有关指定投放大纲的详细信息，请参阅此[部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根据投放完成可用的字段。
1. 可能存在两种情况：

   * 如果要调用优惠引擎，请选中&#x200B;**[!UICONTROL Restrict the number of propositions selected]**&#x200B;框。 指定优惠空间和将在投放中显示的建议数。

     优惠引擎将考虑优惠权重和资格规则。

   * 如果不选中此框，则将显示投放概要中的所有选件，而不调用选件引擎。

   预览会考虑投放中指定的优惠数量。 执行工作流时，将考虑投放大纲中指定的数字。

   ![](assets/int_compo_offre_wf1.png)
