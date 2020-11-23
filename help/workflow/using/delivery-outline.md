---
solution: Campaign Classic
product: campaign
title: 投放概要
description: 进一步了解投放概要工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# 投放概要{#delivery-outline}

投放概要 **允许您** 在活动工作流中使用大纲。 大纲必须事先在活动中创建。

有关Adobe Campaign中投放概要的详细信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活动，您只需选择您喜欢的大纲以及计划的联系日期。 您可以通过添加字体或类型规则来添加筛选规则。

## 示例：通过优惠插入投放概要 {#example--inserting-an-offer-via-a-delivery-outline}

投放概要 **活动** (在活动工作流中可用)允许您展示在投放概要中引用的，这些优惠来自当前进行中的活动。

>[!NOTE]
>
>必 **须安装** Interaction包。

1. 在工作流中，添加投放概要活动后再添加投放活动。
1. 在“投放概要”活动中，指定要使用的轮廓。

   有关指定投放概要的详细信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根据您的投放填写可用字段。
1. 可能有两种情况：

   * 如果要调用优惠引擎，请选中该 **[!UICONTROL Restrict the number of propositions selected]** 框。 指定优惠空间和将在投放中显示的主张数。

      优惠权重和合格规则将由优惠引擎考虑。

   * 如果不选中此框，将显示投放概要中的所有优惠，而无需调用优惠引擎。

   预览会考虑在投放中指定的优惠数。 执行工作流时，它是在投放概要中指定的已考虑的编号。

   ![](assets/int_compo_offre_wf1.png)

