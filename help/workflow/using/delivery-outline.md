---
product: campaign
title: 投放概要
description: 了解有关投放概要工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 投放概要{#delivery-outline}



此 **投放概要** 允许您在营销活动工作流中使用大纲。 必须预先在营销活动中创建大纲。

有关Adobe Campaign中的投放概要的更多信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

要配置活动，您只需选择喜欢的大纲以及计划的联系日期即可。 您可以通过添加分类或分类规则来添加筛选规则。

## 示例：通过投放大纲插入选件 {#example--inserting-an-offer-via-a-delivery-outline}

此 **投放概要** 通过营销活动工作流中可用的活动，可显示当前营销活动在投放概要中引用的优惠。

>[!NOTE]
>
>此 **互动** 必须安装软件包。

1. 在工作流中，添加投放概要活动，然后再添加投放活动。
1. 在投放大纲活动中，指定要使用的大纲。

   有关指定投放大纲的更多信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. 根据投放完成可用字段。
1. 有两种可能的情况：

   * 如果要调用优惠引擎，请检查 **[!UICONTROL Restrict the number of propositions selected]** 盒子。 指定优惠空间和将在投放中显示的建议数量。

      优惠引擎将考虑优惠权重和资格规则。

   * 如果不选中此框，则投放概要中的所有优惠都将显示，而无需调用优惠引擎。

   预览会考虑投放中指定的优惠数量。 执行工作流时，将考虑投放大纲中指定的数字。

   ![](assets/int_compo_offre_wf1.png)
