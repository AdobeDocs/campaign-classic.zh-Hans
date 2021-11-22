---
product: campaign
title: 使用聚合
description: 了解如何使用聚合
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---

# 使用聚合{#using-aggregates}

![](../../assets/common.svg)

此用例详细说明了如何自动识别添加到数据库的最后一个收件人。

使用以下过程，将数据库中收件人的创建日期与使用聚合创建收件人的最后一个已知日期进行比较。 同日创建的所有收件人也将被选中。

执行 **创建日期=最大值（创建日期）** 在收件人上键入过滤器，则必须运行工作流才能执行以下步骤：

1. 使用基本查询检索数据库收件人。 有关此步骤的更多信息，请参阅 [创建查询](query.md#creating-a-query).
1. 使用 **最大（创建日期）** 聚合函数。
1. 将每个收件人链接到聚合函数会生成相同的架构。
1. 通过编辑的架构使用聚合过滤收件人。

![](assets/datamanagement_usecase_1.png)

## 步骤1:计算聚合结果 {#step-1--calculating-the-aggregate-result}

1. 创建查询。 在此，目标是在数据库中所有收件人中计算上次已知创建日期。 因此，查询不包含过滤器。
1. 选择 **[!UICONTROL Add data]**。
1. 在打开的窗口中，选择 **[!UICONTROL Data linked to the filtering dimension]** then **[!UICONTROL Filtering dimension data]**.
1. 在 **[!UICONTROL Data to add]** 窗口中，添加一个列，该列将计算 **创建日期** 字段。 您可以使用表达式编辑器或输入 **max(@created)** 直接输入 **[!UICONTROL Expression]** 列。 然后，单击 **[!UICONTROL Finish]** 按钮。

   ![](assets/datamanagement_usecase_2.png)

1. 单击 **[!UICONTROL Edit additional data]**，然后单击 **[!UICONTROL Advanced parameters...]**。勾选 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 选项。

   此选项可确保不会因此显示所有收件人，并且不会保留明确添加的数据。 在这种情况下，它是指收件人的上次创建日期。

   保持选中 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 选项。

## 步骤2:链接收件人和聚合函数结果 {#step-2--linking-the-recipients-and-the-aggregation-function-result}

要将处理收件人的查询链接到执行聚合函数计算的查询，您必须使用架构编辑活动。

1. 将收件人的查询定义为主集。
1. 在 **[!UICONTROL Links]** 选项卡，添加新链接并在打开的窗口中输入以下信息：

   * 选择与聚合相关的临时架构。 此架构的数据将添加到主集的成员中。
   * 选择 **[!UICONTROL Use a simple join]** 将聚合结果链接到主集的每个收件人。
   * 最后，指定链接为 **[!UICONTROL Type 11 simple link]**.

   ![](assets/datamanagement_usecase_3.png)

因此，聚合结果链接到每个收件人。

## 步骤3:使用聚合过滤收件人。 {#step-3--filtering-recipients-using-the-aggregate-}

建立链接后，聚合结果和收件人构成同一临时架构的一部分。 因此，可以在架构上创建过滤器，以比较收件人的创建日期和由聚合函数表示的最后一个已知创建日期。 此过滤器使用拆分活动执行。

1. 在 **[!UICONTROL General]** 选项卡，选择 **收件人** 作为定向维度和 **编辑架构** 作为筛选维度（用于筛选集客过渡架构活动）。
1. 在 **[!UICONTROL subsets]** 选项卡，选择 **[!UICONTROL Add a filtering condition on the inbound population]** 然后单击 **[!UICONTROL Edit...]**.
1. 使用表达式编辑器，在收件人的创建日期和由聚合计算的创建日期之间添加等同条件。

   数据库中的日期类型字段通常保存为毫秒。 因此，您必须将这些参数延长一天，以避免仅检索在毫秒内创建的收件人。

   为此，请使用 **ToDate** 函数，表达式编辑器中提供，可将日期和小时数转换为简单日期。

   因此，要用于标准的表达式为：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`，其中expr####与聚合函数查询中指定的聚合相关。

   ![](assets/datamanagement_usecase_4.png)

因此，拆分活动的结果与在上次已知创建日期的同一天创建的收件人有关。

然后，您可以添加其他活动（如列表更新或投放）以扩充您的工作流。
