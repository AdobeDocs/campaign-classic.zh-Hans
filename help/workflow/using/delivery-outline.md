---
title: 交付大纲
seo-title: 交付大纲
description: 交付大纲
seo-description: null
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# 交付大纲{#delivery-outline}

分发大纲允许您在营销活动工作流中使用大纲。 大纲必须事先在营销活动中创建。

有关Adobe Campaign中的交付大纲的详细信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活动，您只需选择您喜欢的大纲以及计划的联系日期。 您可以通过添加类型或类型规则来添加过滤规则。

## 示例：通过分发大纲插入选件 {#example--inserting-an-offer-via-a-delivery-outline}

通过营销活动工作流中提供的分发大纲活动，您可以展示当前营销活动在分发大纲中引用的选件。

>[!NOTE]
>
>必 **须安装** Interaction包。

1. 在工作流中，在添加分发活动之前添加分发大纲活动。
1. 在交付大纲活动中，指定要使用的大纲。

   有关指定交付大纲的详细信息，请参阅此 [部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根据您的分发填写可用字段。
1. 有两种可能的情况：

   * 如果要调用选件引擎，请选中该 **[!UICONTROL Restrict the number of propositions selected]** 框。 指定优惠空间和将在交付中展示的建议数。

      选件引擎将考虑选件权重和资格规则。

   * 如果不选中此框，则无需调用选件引擎即可显示交付大纲中的所有选件。
   预览会考虑在交付中指定的选件数量。 执行工作流时，它是在交付大纲中指定并考虑到的数字。

   ![](assets/int_compo_offre_wf1.png)

