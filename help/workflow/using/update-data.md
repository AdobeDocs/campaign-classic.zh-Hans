---
product: campaign
title: 更新数据
description: 了解有关更新数据工作流活动的更多信息
feature: Workflows, Targeting Activity, Data Management
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 4%

---

# 更新数据{#update-data}



An **更新数据**-type活动对数据库中的字段执行批量更新。

## 操作类型 {#operation-type}

此 **[!UICONTROL Operation type]** 字段用于选择要对数据库中的数据执行的流程：

* **[!UICONTROL Insert or update]**：添加数据或更新数据（如果已添加）。
* **[!UICONTROL Insert]**：仅添加数据。
* **[!UICONTROL Update]**：仅更新数据。
* **[!UICONTROL Update and merge collections]**：更新数据并选择一个主记录，然后链接链接到此主记录中重复项的元素。 然后，可以删除重复项而不创建孤立的附加元素。
* **[!UICONTROL Delete]**：删除数据。

![](assets/s_advuser_update_data_1.png)

此 **[!UICONTROL Batch size]** 字段允许您选择要更新的集客过渡元素数量。 例如，如果您声明500，则处理的前500条记录将被更新。

## 记录标识 {#record-identification}

指定如何识别数据库中的记录：

* 如果数据条目与现有的定向维度相关，请选择 **[!UICONTROL By directly using the targeting dimension]** 选项，然后在以下位置选择它： **[!UICONTROL Updated dimension]** 字段。

  您可以使用以下图标显示所选维度的字段： **[!UICONTROL Edit this link]** 放大镜按钮。

* 否则，请指定一个或多个链接，这些链接将允许识别数据库中的数据或直接使用协调键。

![](assets/s_advuser_update_data_2.png)

## 选择要更新的字段 {#selecting-the-fields-to-be-updated}

使用 **[!UICONTROL Automatically associate fields with the same name]** 选项，以便Adobe Campaign自动标识要更新的字段。

![](assets/s_advuser_update_data_3b.png)

您也可以使用 **[!UICONTROL Insert]** 图标以手动选择要更新的数据库字段。

![](assets/s_advuser_update_data_3.png)

选择要更新的所有字段，并根据需要添加条件。 要实现此目的，请使用 **[!UICONTROL Taken into account if]** 列。条件逐个应用，并与列表中的顺序一致。 使用右侧的箭头可更改更新的顺序。

您可以多次使用同一目标字段。

在 **[!UICONTROL Insert or update]** 操作中，您可以单独选择要应用的营销策划，或为每个字段选择要应用的营销策划。 要实现此目的，请在 **[!UICONTROL Operation]** 列。

![](assets/s_advuser_update_data_5.png)

此 **[!UICONTROL modifiedDate]**， **[!UICONTROL modifiedBy]**， **[!UICONTROL createdDate]** 和 **[!UICONTROL createdBy]** 字段在数据更新期间自动更新，除非在字段更新表中专门配置了它们的管理模式。

仅对至少包含一个差异的记录执行记录更新。 如果值相同，则不执行更新。

此 **[!UICONTROL Advanced parameters]** 链接允许您指定其他选项以处理数据更新和管理重复项。 您还可以：

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. 此选项默认处于自动选中状态。
* **[!UICONTROL Update all columns with matching names]**.
* 指定考虑源元素的条件，在 **[!UICONTROL Enabled if]** 字段。
* 使用表达式指定考虑重复项的条件。 如果您检查 **[!UICONTROL Ignore records which concern the same target]** 选项，则只考虑表达式列表中的第一个。

**[!UICONTROL Generate an outbound transition]**

创建将在执行结束时激活的叫客过渡。 更新通常表示定位工作流结束，因此默认情况下不激活该选项。

**[!UICONTROL Generate an outbound transition for the rejects]**

创建一个叫客过渡，其中包含更新后未正确处理的记录（例如，如果存在重复项）。 更新通常标志着定位工作流的结束，因此默认情况下不会激活该选项。

## 更新和合并收藏集 {#updating-and-merging-collections}

通过更新数据和合并集合，您可以使用来自一个或多个辅助记录的数据来更新记录中包含的数据，以便在需要时仅保留一个。 这些更新由一组规则管理。

>[!NOTE]
>
>通过此选项，还可处理对工作流工作表(targetWorkflow)、投放(targetDelivery)和列表(targetList)中辅助记录的引用。 如果需要，这些链接会显示在您选择字段和集合的列表中。

1. 选择 **[!UICONTROL Update and merge collections]** 操作。

   ![](assets/update_and_merge_collections1.png)

1. 选择链接的优先级顺序。 这允许您标识主记录。 可用链接因集客过渡而异。

   ![](assets/update_and_merge_collections2.png)

1. 选择要移动到主记录的收藏集和要更新的字段。

   输入在标识一个或多个辅助记录后应用于这些记录的规则。 为此，您可以使用表达式生成器。 有关详细信息，请参阅此 [部分](../../platform/using/defining-filter-conditions.md#building-expressions). 例如，通过指定该值是必须保留的所有不同记录中最近更新的值。

   然后，输入规则要考虑的条件。

   最后，指定要执行的更新类型。 例如，您可以选择在更新数据之后删除辅助记录。

   例如，您可以配置包含异构数据（如收件人的订阅列表）的集合的合并。 使用规则，您还可以从辅助记录订阅创建新的订阅历史记录，甚至可以将订阅列表从辅助记录移动到主记录。

1. 通过选择，指定您希望处理辅助记录的顺序 **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

如果定义的规则适用，则辅助记录的数据将与主记录关联。 根据所选择的更新类型，可以删除次要记录。

## 示例：在扩充后更新数据 {#example--update-data-following-an-enrichment}

此 [步骤2：将扩充数据写入“购买”表](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) 用例中详细说明创建回顾列表的部分提供了扩充活动后数据更新的示例。

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件必须指定由这些参数定义的目标。
