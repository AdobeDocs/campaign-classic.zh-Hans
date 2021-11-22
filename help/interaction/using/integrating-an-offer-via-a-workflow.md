---
product: campaign
title: 通过工作流集成优惠
description: 通过工作流集成优惠
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 3%

---

# 通过工作流集成优惠{#integrating-an-offer-via-a-workflow}

![](../../assets/v7-only.svg)

在投放活动本身之外，通过多个工作流活动可定义选件的呈现方式：

* 投放概要
* 扩充
* 优惠引擎
* 单元格优惠

## 投放概要 {#delivery-outline}

利用营销活动工作流中提供的投放概要活动，可显示在当前正在进行的营销活动的投放概要中引用的选件。

1. 在工作流中，添加投放大纲活动后再添加投放活动。
1. 在投放大纲活动中，指定要使用的大纲。

   有关指定投放大纲的更多信息，请参阅 [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) 的双曲余切值。

1. 根据您的投放填写可用字段。
1. 可能有两种情况：

   * 如果要调用选件引擎，请检查 **[!UICONTROL Restrict the number of propositions selected]** 框中。 指定优惠空间以及将在投放中呈现的建议数。

      选件引擎将考虑选件权重和资格规则。

   * 如果不勾选方框，则无需调用选件引擎即会显示投放大纲中的所有选件。
   >[!NOTE]
   >
   >预览会考虑投放中指定的选件数量。 执行工作流时，它是在投放大纲中指定的要考虑的编号。

   ![](assets/int_compo_offre_wf1.png)

## 扩充 {#enrichment}

利用扩充活动，可向投放收件人的选件添加选件或链接。

>[!NOTE]
>
>有关扩充活动的更多信息，请参阅 [工作流指南](../../workflow/using/enrichment.md).

例如，您可以在投放之前扩充收件人查询的数据。

![](assets/int_enrichment_offer1.png)

有两种方法可指定优惠建议。

* 指定选件或选件引擎调用。
* 引用指向选件的链接。

### 指定选件或对选件引擎的调用 {#specifying-an-offer-or-a-call-to-the-offer-engine}

配置查询后(请参阅 [工作流指南](../../workflow/using/query.md)):

1. 添加并打开扩充活动。
1. 在 **[!UICONTROL Enrichment]** 选项卡中，选择 **[!UICONTROL Add data]**。
1. 选择 **[!UICONTROL An offer proposition]** 在要添加的数据类型中。

   ![](assets/int_enrichment_offer2.png)

1. 为要添加的建议指定标识符和标签。
1. 指定选件选择。 可以使用以下两个选项：

   * **[!UICONTROL Search for the best offer in a category]** :选中此选项并指定选件引擎调用参数（选件空间、类别或主题、联系日期、要保留的选件数量）。 引擎将根据这些参数自动计算要添加的选件。 我们建议您完成 **[!UICONTROL Category]** 或 **[!UICONTROL Theme]** 字段，而不是同时使用这两个字段。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** :选中此选项并指定选件空间、特定选件和联系日期，以便直接配置要添加的选件，而无需调用选件引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然后，配置与您选择的渠道对应的投放活动。 有关更多信息，请参阅 [在投放中插入优惠建议](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 中。

   >[!NOTE]
   >
   >可用于预览的建议数取决于扩充活动中执行的配置，而不是直接在投放中执行的任何可能的配置。

### 引用指向选件的链接 {#referencing-a-link-to-an-offer}

您还可以引用扩充活动中选件的链接。

为此，请使用以下过程：

1. 选择 **[!UICONTROL Add data]** 的 **[!UICONTROL Enrichment]** 选项卡。
1. 在选择要添加的数据类型的窗口中，选择 **[!UICONTROL A link]**.
1. 选择要建立的链接类型及其目标。 在这种情况下，目标是选件架构。

   ![](assets/int_enrichment_link1.png)

1. 指定扩充活动（此处为收件人表）中的集客表数据与选件表之间的连接。 例如，您可以将选件代码关联到收件人。

   ![](assets/int_enrichment_link2.png)

1. 然后，配置与您选择的渠道对应的投放活动。 有关更多信息，请参阅 [在投放中插入优惠建议](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 中。

   >[!NOTE]
   >
   >可用于预览的建议数取决于投放中执行的配置。

### 存储优惠排名和权重 {#storing-offer-rankings-and-weights}

默认情况下，当 **扩充** 活动用于提供优惠，其排名和权重不会存储在建议表中。

>[!NOTE]
>
>请记住：的 **[!UICONTROL Offer engine]** 默认情况下，活动会存储此信息。

但是，您可以按如下方式存储此信息：

1. 在扩充活动中创建对选件引擎的调用，该活动放在查询之后和投放活动之前。 请参阅 [指定选件或对选件引擎的调用](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) 中。
1. 在活动的主窗口中，选择 **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. 添加 **[!UICONTROL @rank]** 排名和 **[!UICONTROL @weight]** 选件权重。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 确认添加并保存工作流。

投放会自动存储选件的排名和权重。 此信息显示在投放的 **[!UICONTROL Offers]** 选项卡。

## 优惠引擎 {#offer-engine}

的 **[!UICONTROL Offer engine]** 活动还允许您在投放之前指定对选件引擎的调用。

此活动与通过引擎调用扩充活动的原理相同，方法是在投放之前，使用引擎计算的选件扩充集客群体数据。

![](assets/int_offerengine_activity2.png)

配置查询后(请参阅 [工作流指南](../../workflow/using/query.md)):

1. 添加并打开 **[!UICONTROL Offer engine]** 活动。
1. 填写各种可用字段以指定对选件引擎参数（选件空间、类别或主题、联系日期、要保留的选件数量）的调用。 引擎将根据这些参数自动计算要添加的选件。

   >[!NOTE]
   >
   >警告：如果您使用此活动，则只会存储投放中使用的选件建议。

   ![](assets/int_offerengine_activity1.png)

1. 然后，配置与您选择的渠道对应的投放活动。 有关更多信息，请参阅 [在投放中插入优惠建议](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 中。

## 单元格优惠 {#offers-by-cell}

的 **[!UICONTROL Offers by cell]** 活动允许您将集客群体（例如，通过查询）分发到多个区段，并指定要为其中每个区段显示的选件。

为此，请使用以下过程：

1. 添加 **[!UICONTROL Offers by cell]** 活动，然后将其打开。
1. 在 **[!UICONTROL General]** 选项卡，选择要在其中显示选件的选件空间。
1. 在 **[!UICONTROL Cells]** ，请使用 **[!UICONTROL Add]** 按钮：

   * 使用可用的过滤和限制规则指定子集群体。
   * 然后，选择要向子集显示的选件。 可用的选件是那些符合在上一步中选择的选件环境中的条件选件。

      ![](assets/int_offer_per_cell1.png)

1. 然后，配置与您选择的渠道对应的投放活动。 有关更多信息，请参阅 [在投放中插入优惠建议](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 中。
