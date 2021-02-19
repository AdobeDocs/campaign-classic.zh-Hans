---
solution: Campaign Classic
product: campaign
title: 通过工作流集成优惠
description: 通过工作流集成优惠
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 3%

---


# 通过工作流集成优惠{#integrating-an-offer-via-a-workflow}

在投放活动本身之外，多个工作流活动允许您定义优惠的显示方式：

* 投放概要
* 扩充
* 优惠引擎
* 单元格优惠

## 投放概要 {#delivery-outline}

投放概要活动在活动工作流中可用，它允许您显示在投放概要中引用的当前活动中的优惠。

1. 在工作流中，添加投放概要活动后再添加投放活动。
1. 在“投放概要”活动中，指定要使用的轮廓。

   有关指定投放概要的详细信息，请参阅[活动- MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)指南。

1. 根据您的投放填写可用字段。
1. 有两种可能的情况：

   * 如果要调用优惠引擎，请选中&#x200B;**[!UICONTROL Restrict the number of propositions selected]**&#x200B;框。 指定优惠空间和将在投放中显示的建议数。

      优惠权重和合格规则将由优惠引擎考虑。

   * 如果不选中此框，将在不调用优惠引擎的情况下显示投放概要中的所有优惠。
   >[!NOTE]
   >
   >预览会考虑在投放中指定的优惠数。 执行工作流时，它是在投放概要中指定的数字。

   ![](assets/int_compo_offre_wf1.png)

## 扩充 {#enrichment}

扩充活动允许您添加优惠或指向优惠的投放收件人链接。

>[!NOTE]
>
>有关扩充活动的详细信息，请参阅[工作流指南](../../workflow/using/enrichment.md)中的专用文档。

例如，您可以在收件人查询之前为投放数据进行扩充。

![](assets/int_enrichment_offer1.png)

有两种方法可指定优惠建议。

* 指定优惠或优惠引擎调用。
* 引用指向优惠的链接。

### 指定优惠或对优惠引擎的调用{#specifying-an-offer-or-a-call-to-the-offer-engine}

配置查询后(请参阅[工作流指南](../../workflow/using/query.md)):

1. 添加并打开扩充活动。
1. 在 **[!UICONTROL Enrichment]** 选项卡中，选择 **[!UICONTROL Add data]**。
1. 在要添加的数据类型中选择&#x200B;**[!UICONTROL An offer proposition]**。

   ![](assets/int_enrichment_offer2.png)

1. 为将添加的命题指定标识符和标签。
1. 指定优惠选择。 有两种可能的选项：

   * **[!UICONTROL Search for the best offer in a category]** :选中此选项并指定优惠引擎调用参数(优惠空间、类别或主题、联系日期、要保留的优惠数)。引擎将根据这些参数自动计算要添加的优惠。 我们建议同时完成&#x200B;**[!UICONTROL Category]**&#x200B;或&#x200B;**[!UICONTROL Theme]**&#x200B;字段，而不是同时完成这两个字段。

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** :选中此选项并指定优惠空间、特定优惠和联系日期，以直接配置要添加的优惠，无需调用优惠引擎。

      ![](assets/int_enrichment_offer4.png)

1. 然后，配置与所选投放对应的活动渠道。 有关详细信息，请参阅[将优惠建议插入投放](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)部分。

   >[!NOTE]
   >
   >可用于预览的建议的数量取决于在扩充活动中执行的配置，而不是直接在投放中执行的任何可能的配置。

### 引用指向优惠{#referencing-a-link-to-an-offer}的链接

您还可以引用指向扩充活动中优惠的链接。

要执行此操作，请使用以下过程：

1. 在活动的&#x200B;**[!UICONTROL Enrichment]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Add data]**。
1. 在选择要添加的数据类型的窗口中，选择&#x200B;**[!UICONTROL A link]**。
1. 选择要建立的链接类型及其目标。 在这种情况下，目标是优惠模式。

   ![](assets/int_enrichment_link1.png)

1. 在扩充活动(此处为收件人表)中指定入站表数据与优惠表之间的联接。 例如，您可以将优惠代码链接到收件人。

   ![](assets/int_enrichment_link2.png)

1. 然后，配置与所选投放对应的活动渠道。 有关详细信息，请参阅[将优惠建议插入投放](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)部分。

   >[!NOTE]
   >
   >预览可用的建议数取决于投放中执行的配置。

### 存储优惠排名和权重{#storing-offer-rankings-and-weights}

默认情况下，当使用&#x200B;**扩充**&#x200B;活动来传送优惠时，其排名和权重不会存储在命题表中。

>[!NOTE]
>
>记住：默认情况下，**[!UICONTROL Offer engine]**&#x200B;活动会存储此信息。

但是，您可以按如下方式存储此信息：

1. 在放置在优惠之后和投放活动之前的扩充活动中创建对查询引擎的调用。 请参阅[指定优惠或对优惠引擎的调用](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine)部分。
1. 在活动的主窗口中，选择&#x200B;**[!UICONTROL Edit additional data...]**。

   ![](assets/ita_enrichment_rankweight_1.png)

1. 为排名添加&#x200B;**[!UICONTROL @rank]**&#x200B;列，为优惠权重添加&#x200B;**[!UICONTROL @weight]**。

   ![](assets/ita_enrichment_rankweight_2.png)

1. 确认添加内容并保存工作流。

投放自动存储优惠的排名和权重。 此信息显示在投放的&#x200B;**[!UICONTROL Offers]**&#x200B;选项卡中。

## 优惠引擎 {#offer-engine}

**[!UICONTROL Offer engine]**&#x200B;活动还允许您在投放之前指定对优惠引擎的调用。

该活动与引擎调用的扩充活动工作原理相同，通过在投放之前用引擎计算的优惠丰富入站人口数据。

![](assets/int_offerengine_activity2.png)

配置查询后(请参阅[工作流指南](../../workflow/using/query.md)):

1. 添加并打开&#x200B;**[!UICONTROL Offer engine]**&#x200B;活动。
1. 填写各种可用字段以指定对优惠引擎参数(优惠空间、类别或主题、联系日期、要保留的优惠数)的调用。 引擎将根据这些参数自动计算要添加的优惠。

   >[!NOTE]
   >
   >警告：如果您使用此活动，则只会存储投放中使用的优惠建议。

   ![](assets/int_offerengine_activity1.png)

1. 然后，配置与所选投放对应的活动渠道。 有关详细信息，请参阅[将优惠建议插入投放](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)部分。

## 单元格优惠 {#offers-by-cell}

**[!UICONTROL Offers by cell]**&#x200B;活动允许您将入站人口(例如，从查询)分布到多个区段，并指定每个区段显示的优惠。

要执行此操作，请使用以下过程：

1. 在指定活动填充后添加&#x200B;**[!UICONTROL Offers by cell]**&#x200B;目标，然后打开它。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择要显示优惠空间的优惠。
1. 在&#x200B;**[!UICONTROL Cells]**&#x200B;选项卡中，使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮指定不同的子集：

   * 使用可用的过滤和限制规则指定子集填充。
   * 然后选择要向子集显示的优惠。 可用优惠是在上一步选择的优惠环境上符合条件的。

      ![](assets/int_offer_per_cell1.png)

1. 然后，配置与所选投放对应的活动渠道。 有关详细信息，请参阅[将优惠建议插入投放](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery)部分。

