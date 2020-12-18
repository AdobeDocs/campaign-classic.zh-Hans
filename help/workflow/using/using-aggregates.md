---
solution: Campaign Classic
product: campaign
title: 使用聚合
description: 了解如何使用聚合
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---


# 使用聚合{#using-aggregates}

此用例详细信息如何自动标识添加到收件人库的最后一个数据。

使用以下过程，将收件人库中收件人的创建日期与使用聚合创建的上次已知日期进行比较。 同一天创建的所有收件人也将被选中。

要在收件人上执行&#x200B;**创建日期= max（创建日期）**&#x200B;类型筛选器，必须运行工作流以执行以下步骤：

1. 使用基本收件人检索查询库。 有关此步骤的详细信息，请参阅[创建查询](../../workflow/using/query.md#creating-a-query)。
1. 使用从&#x200B;**max（创建日期）**&#x200B;聚合函数生成的结果计算创建收件人的上次已知日期。
1. 将每个收件人链接到聚合函数会生成相同的模式。
1. 通过编辑的收件人使用聚合过滤模式。

![](assets/datamanagement_usecase_1.png)

## 第1步：计算聚合结果{#step-1--calculating-the-aggregate-result}

1. 创建查询。 此处，目标是计算数据库中所有收件人中的上一个已知创建日期。 因此，查询不包含过滤器。
1. 选择 **[!UICONTROL Add data]**。
1. 在打开的窗口中，选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**，然后选择&#x200B;**[!UICONTROL Filtering dimension data]**。
1. 在&#x200B;**[!UICONTROL Data to add]**&#x200B;窗口中，添加一列，该列计算收件人表中&#x200B;**创建日期**&#x200B;字段的最大值。 您可以使用表达式编辑器或直接在&#x200B;**[!UICONTROL Expression]**&#x200B;列的字段中输入&#x200B;**max(@created)**。 然后单击&#x200B;**[!UICONTROL Finish]**&#x200B;按钮。

   ![](assets/datamanagement_usecase_2.png)

1. 单击 **[!UICONTROL Edit additional data]**，然后单击 **[!UICONTROL Advanced parameters...]**。勾选 **[!UICONTROL Disable automatic adding of the primary keys of the targeting dimension]** 选项。

   此选项可确保不显示所有收件人，并且不保留显式添加的数据。 在本例中，它指创建收件人的最后一个日期。

   保持选中 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 选项。

## 第2步：链接收件人和聚合函数结果{#step-2--linking-the-recipients-and-the-aggregation-function-result}

要将处理收件人的查询链接到执行聚合函数计算的查询，必须使用模式编辑活动。

1. 将收件人的查询定义为主集。
1. 在&#x200B;**[!UICONTROL Links]**&#x200B;选项卡中，添加新链接，并在窗口中输入如下信息：

   * 选择与模式相关的临时聚合。 此模式的数据将添加到主集的成员中。
   * 选择&#x200B;**[!UICONTROL Use a simple join]**&#x200B;将聚合结果链接到主集的每个收件人。
   * 最后，指定该链接为&#x200B;**[!UICONTROL Type 11 simple link]**。

   ![](assets/datamanagement_usecase_3.png)

因此，聚合结果链接到每个收件人。

## 第3步：使用收件人筛选聚合。{#step-3--filtering-recipients-using-the-aggregate-}

一旦建立了链接，聚合结果和收件人构成同一临时模式的一部分。 因此，可以在模式上创建过滤器，以比较收件人的创建日期和由聚合函数表示的最后已知创建日期。 此过滤器使用拆分活动执行。

1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择&#x200B;**收件人**&#x200B;作为定位维度，选择&#x200B;**编辑模式**&#x200B;作为过滤维度(以过滤入站过渡活动)。
1. 在&#x200B;**[!UICONTROL subsets]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**，然后单击&#x200B;**[!UICONTROL Edit...]**。
1. 使用表达式编辑器，在收件人的创建日期和聚合计算的创建日期之间添加一个等同标准。

   数据库中的日期类型字段通常保存到毫秒。 因此，您必须将这些收件人延长整天，以避免检索仅在同一毫秒内创建的数据。

   为此，请使用表达式编辑器中提供的&#x200B;**ToDate**&#x200B;函数，该函数将日期和小时转换为简单日期。

   因此，要用于该标准的表达式是：

   * **[!UICONTROL Expression]**: `toDate([target/@created])`.
   * **[!UICONTROL Value]**: `toDate([datemax/expr####])`，其中expr####与聚合函数查询中指定的聚合相关。

   ![](assets/datamanagement_usecase_4.png)

因此，拆分活动的结果与创建与上次已知创建日期相同的日期相关的收件人。

然后，您可以添加其他活动，如列表更新或投放，以丰富您的工作流。
