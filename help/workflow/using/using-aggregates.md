---
title: 使用聚合
description: 了解如何使用聚合
page-status-flag: never-activated
uuid: 70556745-56b2-4f22-bbc5-7f8106fb0d4a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9ca649b4-2226-4cfe-bae1-4632c421975b
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---


# 使用聚合{#using-aggregates}

此用例详细信息如何自动标识添加到收件人库的最后一个数据。

使用以下过程，将收件人库中收件人的创建日期与使用聚合创建的上次已知日期进行比较。 同一天创建的所有收件人也将被选中。

要对收件人执 **行“创建日期=最大(创建日期** )”类型筛选器，必须运行工作流以执行以下步骤：

1. 使用基本收件人检索查询库。 有关此步骤的详细信息，请参 [阅创建查询](../../workflow/using/query.md#creating-a-query)。
1. 使用最大（创建日期）聚合函数生成的结果计算创建收件人 **的上次已知日期** 。
1. 将每个收件人链接到聚合函数会生成相同的模式。
1. 通过编辑的收件人使用聚合过滤模式。

![](assets/datamanagement_usecase_1.png)

## 第1步：计算聚合结果 {#step-1--calculating-the-aggregate-result}

1. 创建查询。 此处，目标是计算数据库中所有收件人中的上一个已知创建日期。 因此，查询不包含过滤器。
1. 选择 **[!UICONTROL Add data]**。
1. 在打开的窗口中，选择 **[!UICONTROL Data linked to the filtering dimension]** 然后 **[!UICONTROL Filtering dimension data]**。
1. 在窗 **[!UICONTROL Data to add]** 口中，添加一列，它计算收件人表 **中“创建日期** ”字段的最大值。 您可以使用表达式编辑器 **或直接在列的字** 段中输入 **[!UICONTROL Expression]** max(@created)。 Then click the **[!UICONTROL Finish]** button.

   ![](assets/datamanagement_usecase_2.png)

1. 单击 **[!UICONTROL Edit additional data]**，然后单击 **[!UICONTROL Advanced parameters...]**。勾选 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 选项。

   此选项可确保不显示所有收件人，并且不保留显式添加的数据。 在本例中，它指创建收件人的最后一个日期。

   保持选中 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 选项。

## 第2步：链接收件人和聚合函数结果 {#step-2--linking-the-recipients-and-the-aggregation-function-result}

要将处理收件人的查询链接到执行聚合函数计算的查询，必须使用模式编辑活动。

1. 将收件人的查询定义为主集。
1. 在选项卡 **[!UICONTROL Links]** 中，添加新链接并在窗口中输入以下信息：

   * 选择与模式相关的临时聚合。 此模式的数据将添加到主集的成员中。
   * 选 **[!UICONTROL Use a simple join]** 择将聚合结果链接到主集的每个收件人。
   * 最后，指定链接为 **[!UICONTROL Type 11 simple link]**。

   ![](assets/datamanagement_usecase_3.png)

因此，聚合结果链接到每个收件人。

## 第3步：使用收件人筛选聚合。 {#step-3--filtering-recipients-using-the-aggregate-}

一旦建立了链接，聚合结果和收件人构成同一临时模式的一部分。 因此，可以在模式上创建过滤器，以比较收件人的创建日期和由聚合函数表示的最后已知创建日期。 此过滤器使用拆分活动执行。

1. 在选 **[!UICONTROL General]** 项卡中，选 **择收件人** 作为定位维度, **选择编辑模式作为过滤维度** (以过滤入站过渡模式活动)。
1. 在选项 **[!UICONTROL subsets]** 卡中，选 **[!UICONTROL Add a filtering condition on the inbound population]** 择，然后单击 **[!UICONTROL Edit...]**。
1. 使用表达式编辑器，在收件人的创建日期和聚合计算的创建日期之间添加一个等同标准。

   数据库中的日期类型字段通常保存到毫秒。 因此，您必须将这些收件人延长整天，以避免检索仅在同一毫秒内创建的数据。

   为此，请使用表达式 **编辑器中** 的ToDate函数，该函数可将日期和小时数转换为简单日期。

   因此，要用于该标准的表达式是：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`，其中expr####与聚合函数查询中指定的聚合相关。

   ![](assets/datamanagement_usecase_4.png)

因此，拆分活动的结果与创建与上次已知创建日期相同的日期相关的收件人。

然后，您可以添加其他活动，如列表更新或投放，以丰富您的工作流。
