---
title: 通过工作流集成选件
seo-title: 通过工作流集成选件
description: 通过工作流集成选件
seo-description: null
page-status-flag: never-activated
uuid: 57c4d4e0-6594-46f0-b9ce-2c689fb2eaa2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
discoiquuid: 6e27caea-1f1a-457d-bdec-1f93a12b01cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# 通过工作流集成选件{#integrating-an-offer-via-a-workflow}

在交付活动本身之外，多个工作流活动允许您定义选件的呈现方式：

* 交付大纲
* 扩充
* 优惠引擎
* 按单元格列出的优惠

## 交付大纲 {#delivery-outline}

通过营销活动工作流中提供的分发大纲活动，您可以展示当前营销活动在分发大纲中引用的选件。

1. 在工作流中，在添加分发活动之前添加分发大纲活动。
1. 在交付大纲活动中，指定要使用的大纲。

   有关指定交付大纲的详细信息，请参阅 [Campaign - MRM指南](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) 。

1. 根据您的分发填写可用字段。
1. 有两种可能的情况：

   * 如果要调用选件引擎，请选中该 **[!UICONTROL Restrict the number of propositions selected]** 框。 指定优惠空间和将在交付中展示的建议数。

      选件引擎将考虑选件权重和资格规则。

   * 如果不选中此框，则无需调用选件引擎即可显示交付大纲中的所有选件。
   >[!NOTE]
   >
   >预览会考虑在交付中指定的选件数量。 执行工作流时，它是在交付大纲中指定并考虑到的数字。

   ![](assets/int_compo_offre_wf1.png)

## 扩充 {#enrichment}

通过丰富化活动，您可以为交付收件人添加选件或指向选件的链接。

>[!NOTE]
>
>有关丰富化活动的详细信息，请参阅工作流指南中的专 [用文档](../../workflow/using/enrichment.md)。

例如，您可以在分发之前为收件人查询丰富数据。

![](assets/int_enrichment_offer1.png)

有两种方法可指定选件命题。

* 指定选件或选件引擎调用。
* 引用指向选件的链接。

### 指定选件或对选件引擎的调用 {#specifying-an-offer-or-a-call-to-the-offer-engine}

配置查询后(请参阅工作 [流指南](../../workflow/using/query.md)):

1. 添加和开展丰富化活动。
1. 在选项卡 **[!UICONTROL Enrichment]** 中，选择 **[!UICONTROL Add data]**。
1. 在要 **[!UICONTROL An offer proposition]** 添加的数据类型中进行选择。

   ![](assets/int_enrichment_offer2.png)

1. 为将添加的主张指定标识符和标签。
1. 指定选件选择。 这有两个可能的选项：

   * **[!UICONTROL Search for the best offer in a category]** :选中此选项并指定选件引擎调用参数（选件空间、类别或主题、联系日期、要保留的选件数量）。 引擎将根据这些参数自动计算要添加的选件。 我们建议填写 **[!UICONTROL Category]** 或字 **[!UICONTROL Theme]** 段，而不是同时填写两者。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** :选中此选项并指定选件空间、特定选件和联系日期，以直接配置要添加的选件，而无需调用选件引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然后，配置与所选渠道对应的交付活动。 有关此问题的详细信息，请参 [阅将选件建议插入交付部分](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

   >[!NOTE]
   >
   >可用于预览的建议的数量取决于在富集活动中执行的配置，而不是直接在交付中执行的任何可能的配置。

### 引用指向选件的链接 {#referencing-a-link-to-an-offer}

您还可以在丰富化活动中引用选件的链接。

为此，请使用以下过程：

1. 在活 **[!UICONTROL Add data]** 动的选项卡中进行 **[!UICONTROL Enrichment]** 选择。
1. 在选择要添加的数据类型的窗口中，选择 **[!UICONTROL A link]**。
1. 选择要建立的链接类型及其目标。 在这种情况下，目标是选件架构。

   ![](assets/int_enrichment_link1.png)

1. 指定丰富化活动（此处为收件人表）中的入站表数据与选件表之间的连接。 例如，您可以将选件代码链接到收件人。

   ![](assets/int_enrichment_link2.png)

1. 然后，配置与所选渠道对应的交付活动。 有关此问题的详细信息，请参 [阅将选件建议插入交付部分](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

   >[!NOTE]
   >
   >预览可用的建议数取决于交付中执行的配置。

### 存储优惠排名和权重 {#storing-offer-rankings-and-weights}

默认情况下，当利用丰 **富活动** 来提供优惠时，其排名和权重不会存储在命题表中。

>[!NOTE]
>
>记住：默认 **[!UICONTROL Offer engine]** 情况下，活动确实会存储此信息。

但是，您可以按如下方式存储此信息：

1. 在查询之后和交付活动之前放置的丰富化活动中创建对选件引擎的调用。 请参阅指 [定选件或调用选件引擎部分](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) 。
1. 在活动的主窗口中，选择 **[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 添加 **[!UICONTROL @rank]** 排名列和选 **[!UICONTROL @weight]** 件权重列。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 确认您的添加并保存您的工作流。

交付自动存储选件的排名和权重。 此信息显示在分发的选项卡 **[!UICONTROL Offers]** 中。

## 优惠引擎 {#offer-engine}

通过 **[!UICONTROL Offer engine]** 此活动，您还可以在交付之前指定对选件引擎的调用。

通过在交付之前使用引擎计算的优惠来丰富入站人口数据，该活动与使用引擎调用的富集活动遵循相同的原则。

![](assets/int_offerengine_activity2.png)

配置查询后(请参阅工作 [流指南](../../workflow/using/query.md)):

1. 添加和打开活 **[!UICONTROL Offer engine]** 动。
1. 填写各种可用字段以指定对选件引擎参数（选件空间、类别或主题、联系日期、要保留的选件数量）的调用。 引擎将根据这些参数自动计算要添加的选件。

   >[!NOTE]
   >
   >警告：如果您使用此活动，则仅存储交付中使用的选件建议。

   ![](assets/int_offerengine_activity1.png)

1. 然后，配置与所选渠道对应的交付活动。 有关此问题的详细信息，请参 [阅将选件建议插入交付部分](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

## 按单元格列出的优惠 {#offers-by-cell}

通过 **[!UICONTROL Offers by cell]** 此活动，您可以将入站人口（例如，从查询）分发到多个区段，并指定要为每个区段显示的选件。

为此，请使用以下过程：

1. 指定目 **[!UICONTROL Offers by cell]** 标人群后，添加活动，然后打开它。
1. 在选 **[!UICONTROL General]** 项卡中，选择要在其中展示选件的选件空间。
1. 在选项卡 **[!UICONTROL Cells]** 中，使用按钮指定不同的子 **[!UICONTROL Add]** 集：

   * 使用可用的过滤和限制规则指定子集填充。
   * 然后，选择要向子集展示的选件。 可用的选件是在上一步选择的选件环境中符合条件的选件。

      ![](assets/int_offer_per_cell1.png)

1. 然后，配置与所选渠道对应的交付活动。 有关此问题的详细信息，请参 [阅将选件建议插入交付部分](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) 。

