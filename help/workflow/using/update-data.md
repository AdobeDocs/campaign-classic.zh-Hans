---
solution: Campaign Classic
product: campaign
title: 更新数据
description: 了解有关更新数据工作流程的更多信息活动
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

**更新数据**&#x200B;类型活动执行数据库中字段的大量更新。

## 操作类型{#operation-type}

在&#x200B;**[!UICONTROL Operation type]**&#x200B;字段中，您可以选择要对数据库中的数据执行的进程：

* **[!UICONTROL Insert or update]**:添加数据或更新数据（如果已添加）。
* **[!UICONTROL Insert]**:仅添加数据。
* **[!UICONTROL Update]**:仅更新数据。
* **[!UICONTROL Update and merge collections]**:更新数据并选择主记录，然后链接链接到此主记录中重复的元素。然后，可以删除重复，而不创建孤立的附加元素。
* **[!UICONTROL Delete]**：删除数据。

![](assets/s_advuser_update_data_1.png)

在&#x200B;**[!UICONTROL Batch size]**&#x200B;字段中，您可以选择要更新的入站过渡元素数。 例如，如果您声明为500，则处理的前500条记录将更新。

## 记录标识{#record-identification}

指定如何标识数据库中的记录：

* 如果数据条目与现有定位维度相关，请选择&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;选项，然后在&#x200B;**[!UICONTROL Updated dimension]**&#x200B;字段中选择它。

   可使用&#x200B;**[!UICONTROL Edit this link]**&#x200B;放大镜按钮显示所选维度的字段。

* 否则，请指定一个或多个链接，这些链接将启用数据库中数据的标识或直接使用合并关键项。

![](assets/s_advuser_update_data_2.png)

## 选择要更新的字段{#selecting-the-fields-to-be-updated}

使用&#x200B;**[!UICONTROL Automatically associate fields with the same name]**&#x200B;选项，以便Adobe Campaign自动标识要更新的字段。

![](assets/s_advuser_update_data_3b.png)

您还可以使用&#x200B;**[!UICONTROL Insert]**&#x200B;图标手动选择要更新的数据库字段。

![](assets/s_advuser_update_data_3.png)

选择要更新的所有字段，并根据需要添加条件，具体取决于要执行的更新。 要实现此目的，请使用 **[!UICONTROL Taken into account if]** 列。条件会逐个应用，并与列表中的顺序保持一致。 使用右侧的箭头更改更新的顺序。

可以多次使用同一目标字段。

在&#x200B;**[!UICONTROL Insert or update]**&#x200B;操作中，您可以选择要单独应用的活动，也可以为每个字段单独应用。 为此，请在&#x200B;**[!UICONTROL Operation]**&#x200B;列中选择所需的值。

![](assets/s_advuser_update_data_5.png)

**[!UICONTROL modifiedDate]**、**[!UICONTROL modifiedBy]**、**[!UICONTROL createdDate]**&#x200B;和&#x200B;**[!UICONTROL createdBy]**&#x200B;字段在数据更新期间自动更新，除非在字段更新表中专门配置了它们的管理模式。

只对包含至少一个差异的记录执行记录更新。 如果值相同，则不执行更新。

通过&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接，您可以指定其他选项来处理更新数据和管理重复。 您还可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**.默认情况下，会自动选中此选项。
* **[!UICONTROL Update all columns with matching names]**.
* 在&#x200B;**[!UICONTROL Enabled if]**&#x200B;字段中指定考虑源元素的表达式条件。
* 指定考虑使用重复的表达式条件。 如果选中&#x200B;**[!UICONTROL Ignore records which concern the same target]**&#x200B;选项，则只考虑表达式列表中的第一个。

**[!UICONTROL Generate an outbound transition]**

创建将在执行结束时激活的出站过渡。 更新通常表示定位工作流的结束，因此默认情况下不激活该选项。

**[!UICONTROL Generate an outbound transition for the rejects]**

创建出站过渡，其中包含更新后未正确处理的记录(例如，如果有重复)。 更新通常会标记定位工作流的结束，因此默认情况下不会激活该选项。

## 更新和合并集合{#updating-and-merging-collections}

通过更新数据和合并集合，您可以使用一个或多个辅助记录中的数据来更新记录中包含的数据，目的是在需要时仅保留一个记录。 这些更新由一组规则管理。

>[!NOTE]
>
>此选项还允许您处理对工作流工作表(targetWorkflow)、投放(targetDelivery)和列表(targetList)中辅助记录的引用。 如果需要，这些链接将显示在您选择字段和集合的列表中。

1. 选择&#x200B;**[!UICONTROL Update and merge collections]**&#x200B;操作。

   ![](assets/update_and_merge_collections1.png)

1. 选择链接的优先级顺序。 这样您就可以识别主记录。 可用链接因入站过渡而异。

   ![](assets/update_and_merge_collections2.png)

1. 选择要移动到主记录的收藏集和要更新的字段。

   输入一次标识一个或多个辅助记录时适用于这些记录的规则。 要执行此操作，可以使用表达式构建器。 有关更多信息，请参阅此](../../platform/using/defining-filter-conditions.md#building-expressions)章节[。例如，通过指定它是所有必须保留的不同记录中最近更新的值。

   然后输入要考虑规则的条件。

   最后，指定要执行的更新类型。 例如，您可以在更新数据后选择删除辅助记录。

   例如，您可以配置合并包含异构数据的集合，如收件人的订阅列表。 使用规则，您还可以从辅助记录订阅创建新的订阅历史记录，甚至可以将订阅列表从辅助记录移动到主记录。

1. 通过选择&#x200B;**[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**，指定处理辅助记录的顺序。

   ![](assets/update_and_merge_collections3.png)

如果定义的规则适用，辅助记录的数据将与主记录关联。 根据所选的更新类型，可删除辅助记录。

## 示例：更新扩充{#example--update-data-following-an-enrichment}后的数据

[步骤2:将丰富数据写入到用例的“购买”表](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table)部分，该表的详细信息创建重新列表优惠扩充活动后的数据更新示例。

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件都必须指定由这些参数定义的目标。
