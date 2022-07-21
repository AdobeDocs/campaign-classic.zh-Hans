---
product: campaign
title: 更新数据
description: 了解有关更新数据工作流活动的更多信息
feature: Workflows, Targeting Activity, Data Management
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# 更新数据{#update-data}

![](../../assets/v7-only.svg)

安 **更新数据**-type活动对数据库中的字段执行批量更新。

## 操作类型 {#operation-type}

的 **[!UICONTROL Operation type]** 字段，可选择要对数据库中的数据执行的流程：

* **[!UICONTROL Insert or update]**:添加数据或更新（如果已添加）。
* **[!UICONTROL Insert]**:仅添加数据。
* **[!UICONTROL Update]**:仅更新数据。
* **[!UICONTROL Update and merge collections]**:更新数据并选择主记录，然后链接链接到此主记录中重复项的元素。 然后，可以删除重复项，而无需创建孤立的附加元素。
* **[!UICONTROL Delete]**：删除数据。

![](assets/s_advuser_update_data_1.png)

的 **[!UICONTROL Batch size]** 字段，可选择要更新的集客过渡元素数量。 例如，如果您声明500，则处理的前500条记录将会更新。

## 记录标识 {#record-identification}

指定如何识别数据库中的记录：

* 如果数据条目与现有定向维度相关，请选择 **[!UICONTROL By directly using the targeting dimension]** 选项，并在 **[!UICONTROL Updated dimension]** 字段。

   您可以使用 **[!UICONTROL Edit this link]** 放大镜按钮。

* 否则，请指定一个或多个链接，这些链接将允许标识数据库中的数据或直接使用协调键值。

![](assets/s_advuser_update_data_2.png)

## 选择要更新的字段 {#selecting-the-fields-to-be-updated}

使用 **[!UICONTROL Automatically associate fields with the same name]** 选项，以便Adobe Campaign自动识别要更新的字段。

![](assets/s_advuser_update_data_3b.png)

您还可以使用 **[!UICONTROL Insert]** 图标以手动选择要更新的数据库字段。

![](assets/s_advuser_update_data_3.png)

选择要更新的所有字段，并根据需要添加条件，具体取决于要执行更新的字段。 要实现此目的，请使用 **[!UICONTROL Taken into account if]** 列。条件会依次应用，并符合列表中的顺序。 使用右侧的箭头更改更新的顺序。

您可以多次使用同一目标字段。

在 **[!UICONTROL Insert or update]** 操作时，您可以单独或为每个字段选择要应用的营销活动。 为此，请在 **[!UICONTROL Operation]** 列。

![](assets/s_advuser_update_data_5.png)

的 **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** 和 **[!UICONTROL createdBy]** 字段会在数据更新期间自动更新，除非在字段更新表中专门配置了其管理模式。

只对包含至少一个差异的记录执行记录更新。 如果值相同，则不执行更新。

的 **[!UICONTROL Advanced parameters]** 链接允许您指定其他选项来处理更新数据和管理重复项。 您还可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. 默认情况下，此选项会自动选中。
* **[!UICONTROL Update all columns with matching names]**.
* 指定在 **[!UICONTROL Enabled if]** 字段。
* 指定使用表达式考虑重复项的条件。 如果您选中 **[!UICONTROL Ignore records which concern the same target]** 选项中，将仅考虑表达式列表中的第一个参数。

**[!UICONTROL Generate an outbound transition]**

创建将在执行结束时激活的叫客过渡。 更新通常表示定位工作流的结束，因此默认情况下不会激活选项。

**[!UICONTROL Generate an outbound transition for the rejects]**

创建叫客过渡，其中包含更新后未正确处理的记录（例如，如果存在重复项）。 更新通常会标记定向工作流的结尾，因此默认情况下不会激活选项。

## 更新和合并收藏集 {#updating-and-merging-collections}

通过更新数据和合并集合，您可以使用一个或多个辅助记录中的数据来更新记录中包含的数据，以便在需要时仅保留一个。 这些更新由一组规则管理。

>[!NOTE]
>
>此选项还允许您处理来自工作流工作表(targetWorkflow)、投放(targetDelivery)和列表(targetList)的辅助记录的引用。 如果需要，这些链接会显示在您选择字段和收藏集的列表中。

1. 选择 **[!UICONTROL Update and merge collections]** 操作。

   ![](assets/update_and_merge_collections1.png)

1. 选择链接的优先级顺序。 这样可以识别主记录。 可用链接因集客过渡而异。

   ![](assets/update_and_merge_collections2.png)

1. 选择要移动到主记录和要更新的字段的集合。

   输入规则，在一个或多个辅助记录被识别后应用于这些记录。 要实现此目的，您可以使用表达式生成器。 有关更多信息，请参阅此](../../platform/using/defining-filter-conditions.md#building-expressions)章节[。例如，通过指定它是所有必须保留的不同记录中最近更新的值。

   然后，输入要考虑规则的条件。

   最后，指定要执行的更新类型。 例如，您可以选择在更新数据后删除辅助记录。

   例如，您可以配置包含异构数据（如收件人的订阅列表）的集合的合并。 使用规则，您还可以从辅助记录订阅创建新的订阅历史记录，甚至将订阅列表从辅助记录移动到主记录。

1. 通过选择 **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

如果定义的规则适用，则辅助记录的数据将与主记录关联。 根据所选的更新类型，可删除次记录。

## 示例：扩充后更新数据 {#example--update-data-following-an-enrichment}

的 [步骤2:将扩充数据写入“购买”表](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) 在用例的“详细信息”部分中，创建记录列表提供了扩充活动后数据更新的示例。

## 输入参数 {#input-parameters}

* tableName
* 模式

每个集客事件必须指定由这些参数定义的目标。
