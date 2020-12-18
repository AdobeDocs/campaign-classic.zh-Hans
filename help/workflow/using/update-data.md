---
solution: Campaign Classic
product: campaign
title: 更新数据
description: 进一步了解更新数据工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---


# 更新数据{#update-data}

**更新活动**&#x200B;类型执行数据库中字段的大量更新。

## 操作类型{#operation-type}

在&#x200B;**[!UICONTROL Operation type]**&#x200B;字段中，您可以选择要对数据库中的数据执行的进程：

* **[!UICONTROL Insert or update]**:添加数据或更新数据（如果已添加）。
* **[!UICONTROL Insert]**:仅添加数据。
* **[!UICONTROL Update]**:仅更新数据。
* **[!UICONTROL Update and merge collections]**:更新数据并选择主记录，然后链接链接到此主记录中重复的元素。然后，无需创建孤立的附加元素即可删除重复。
* **[!UICONTROL Delete]**：删除数据。

![](assets/s_advuser_update_data_1.png)

在&#x200B;**[!UICONTROL Batch size]**&#x200B;字段中，可以选择要更新的入站过渡元素数。 例如，如果您声明为500，则处理的前500条记录将更新。

## 记录标识{#record-identification}

指定如何在数据库中标识记录：

* 如果数据条目与现有定位维度相关，请选择&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;选项，然后在&#x200B;**[!UICONTROL Updated dimension]**&#x200B;字段中选择它。

   可使用&#x200B;**[!UICONTROL Edit this link]**&#x200B;放大镜按钮显示所选维度的字段。

* 否则，指定一个或多个链接，这些链接将启用数据库中数据的标识或直接使用合并关键项。

![](assets/s_advuser_update_data_2.png)

## 选择要更新的字段{#selecting-the-fields-to-be-updated}

使用&#x200B;**[!UICONTROL Automatically associate fields with the same name]**&#x200B;选项，以便Adobe Campaign自动标识要更新的字段。

![](assets/s_advuser_update_data_3b.png)

还可以使用&#x200B;**[!UICONTROL Insert]**&#x200B;图标手动选择要更新的数据库字段。

![](assets/s_advuser_update_data_3.png)

选择所有要更新的字段，并根据要执行的更新添加条件（如有必要）。 要实现此目的，请使用 **[!UICONTROL Taken into account if]** 列。条件会一个接一个地应用，并与列表中的顺序保持一致。 使用右侧的箭头更改更新的顺序。

可以多次使用同一目标字段。

在&#x200B;**[!UICONTROL Insert or update]**&#x200B;操作中，您可以选择要单独应用的活动，也可以选择每个字段。 为此，请在&#x200B;**[!UICONTROL Operation]**&#x200B;列中选择所需的值。

![](assets/s_advuser_update_data_5.png)

**[!UICONTROL modifiedDate]**、**[!UICONTROL modifiedBy]**、**[!UICONTROL createdDate]**&#x200B;和&#x200B;**[!UICONTROL createdBy]**&#x200B;字段在数据更新期间自动更新，除非在字段更新表中专门配置了它们的管理模式。

只对包含至少一个差异的记录执行记录更新。 如果值相同，则不执行更新。

通过&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接，您可以指定其他选项来处理更新数据和管理重复。 您还可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**.默认情况下，此选项会自动选中。
* **[!UICONTROL Update all columns with matching names]**.
* 在&#x200B;**[!UICONTROL Enabled if]**&#x200B;字段中指定使用表达式来考虑源元素的条件。
* 指定使用重复考虑表达式的条件。 如果选中&#x200B;**[!UICONTROL Ignore records which concern the same target]**&#x200B;选项，则只考虑表达式列表中的第一个选项。

**[!UICONTROL Generate an outbound transition]**

创建将在执行结束时激活的出站过渡。 更新通常表示定位工作流的结束，因此默认情况下不激活该选项。

**[!UICONTROL Generate an outbound transition for the rejects]**

创建一个出站过渡，其中包含更新后未正确处理的记录(例如，如果有重复)。 更新通常标记定位工作流的结束，因此默认情况下不激活该选项。

## 更新和合并集合{#updating-and-merging-collections}

通过更新数据和合并集合，您可以使用来自一个或多个辅助记录的数据来更新记录中包含的数据，以期在需要时只保留一个。 这些更新由一组规则管理。

>[!NOTE]
>
>此选项还允许您处理对工作流工作表(targetWorkflow)、投放(targetDelivery)和列表(targetList)中辅助记录的引用。 如果需要，这些链接会显示在您选择字段和集合的列表中。

1. 选择&#x200B;**[!UICONTROL Update and merge collections]**&#x200B;操作。

   ![](assets/update_and_merge_collections1.png)

1. 选择链接的优先级顺序。 这允许您识别主记录。 可用链接因入站过渡而异。

   ![](assets/update_and_merge_collections2.png)

1. 选择要移到主记录的集合和要更新的字段。

   输入一次识别一个或多个辅助记录时适用于这些记录的规则。 为此，可使用表达式生成器。 有关更多信息，请参阅此](../../platform/using/defining-filter-conditions.md#building-expressions)章节[。例如，通过指定它是所有必须保留的不同记录中最近更新的值。

   然后输入要考虑规则的条件。

   最后，指定要执行的更新类型。 例如，您可以在更新数据后选择删除辅助记录。

   例如，您可以配置合并包含异构数据的集合，如收件人的列表。 使用规则，您还可以从辅助记录订阅创建新的订阅历史记录，甚至可以将订阅的列表从辅助记录移到主记录。

1. 通过选择&#x200B;**[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**，指定要处理辅助记录的顺序。

   ![](assets/update_and_merge_collections3.png)

辅助记录的数据与主记录相关联（如果定义的规则适用）。 根据所选的更新类型，可以删除辅助记录。

## 示例：在扩充{#example--update-data-following-an-enrichment}后更新数据

[步骤2:将丰富数据写入用例的“购买”表](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table)部分，该表&lt;a1/>部分详细信息创建重新列表优惠在扩充活动之后的数据更新示例。

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件必须指定由这些参数定义的目标。
