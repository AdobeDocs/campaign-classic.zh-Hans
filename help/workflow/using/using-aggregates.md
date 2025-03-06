---
product: campaign
title: 使用聚合
description: 了解如何使用聚合
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 1%

---

# 使用聚合{#using-aggregates}



此用例详细说明了如何自动识别添加到数据库中的最后一个收件人。

按照以下流程，将数据库中的收件人创建日期与上次已知使用聚合创建收件人的日期进行比较。 此外，还将选择在同一天创建的所有收件人。

要对收件人执行&#x200B;**创建日期= max （创建日期）**&#x200B;类型过滤器，您必须运行工作流以执行以下步骤：

1. 使用基本查询检索数据库收件人。 有关此步骤的详细信息，请参阅[创建查询](query.md#creating-a-query)。
1. 使用从&#x200B;**max （创建日期）**&#x200B;聚合函数生成的结果计算上次创建收件人的已知日期。
1. 将每个收件人链接到聚合函数会生成相同的模式。
1. 通过编辑后的架构使用聚合筛选收件人。

![](assets/datamanagement_usecase_1.png)

## 步骤1：计算聚合结果 {#step-1--calculating-the-aggregate-result}

1. 创建查询。 在本例中，目标是计算数据库中所有收件人的上次已知创建日期。 因此，查询不包含过滤器。
1. 选择 **[!UICONTROL Add data]**。
1. 在打开的窗口中，依次选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;和&#x200B;**[!UICONTROL Filtering dimension data]**。
1. 在&#x200B;**[!UICONTROL Data to add]**&#x200B;窗口中，添加计算收件人表中&#x200B;**创建日期**&#x200B;字段最大值的列。 您可以使用表达式编辑器或直接在&#x200B;**[!UICONTROL Expression]**&#x200B;列中的字段中输入&#x200B;**max(@created)**。 然后单击&#x200B;**[!UICONTROL Finish]**&#x200B;按钮。

   ![](assets/datamanagement_usecase_2.png)

1. 单击&#x200B;**[!UICONTROL Edit additional data]**，然后单击&#x200B;**[!UICONTROL Advanced parameters...]**。 勾选 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 选项。

   此选项确保不会显示所有收件人，并且不会保留明确添加的数据。 在这种情况下，该日期是指上次创建收件人的日期。

   保持选中 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 选项。

## 步骤2：关联收件人和聚合函数结果 {#step-2--linking-the-recipients-and-the-aggregation-function-result}

要将处理收件人的查询链接到执行聚合函数计算的查询，必须使用模式编辑活动。

1. 将收件人的查询定义为主集。
1. 在&#x200B;**[!UICONTROL Links]**&#x200B;选项卡中，添加新链接，并在打开的窗口中输入信息，如下所示：

   * 选择与聚合相关的临时架构。 此架构的数据将添加到主集的成员中。
   * 选择&#x200B;**[!UICONTROL Use a simple join]**&#x200B;将聚合结果链接到主集的每个收件人。
   * 最后，指定链接为&#x200B;**[!UICONTROL Type 11 simple link]**。

   ![](assets/datamanagement_usecase_3.png)

因此，聚合结果链接到每个收件人。

## 步骤3：使用聚合过滤收件人。 {#step-3--filtering-recipients-using-the-aggregate-}

建立链接后，聚合结果和收件人构成同一临时模式的一部分。 因此，可以在架构上创建过滤器，以比较收件人的创建日期与最后已知创建日期，该日期由聚合函数表示。 此过滤器使用拆分活动执行。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择&#x200B;**收件人**&#x200B;作为定向维度，选择&#x200B;**编辑架构**&#x200B;作为筛选维度（以筛选入站过渡架构活动）。
1. 在&#x200B;**[!UICONTROL subsets]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**，然后单击&#x200B;**[!UICONTROL Edit...]**。
1. 使用表达式编辑器，在收件人的创建日期与聚合计算的创建日期之间添加相等条件。

   数据库中的日期类型字段通常以毫秒为单位保存。 因此，您必须将这些时间延长一整天，以避免检索仅创建该毫秒的收件人。

   为此，请使用表达式编辑器中提供的&#x200B;**ToDate**&#x200B;函数，该函数可将日期和小时转换为简单日期。

   因此，用于标准的表达式为：

   * **[!UICONTROL Expression]**： `toDate([target/@created])`。
   * **[!UICONTROL Value]**： `toDate([datemax/expr####])`，其中expr####与聚合函数查询中指定的聚合相关。

   ![](assets/datamanagement_usecase_4.png)

因此，拆分活动的结果与上次已知创建日期同一天创建的收件人相关。

然后，您可以添加其他活动（如列表更新或投放）以丰富您的工作流。
