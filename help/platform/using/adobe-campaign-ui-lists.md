---
product: campaign
title: 管理和自定义列表
description: 了解如何浏览和配置列表
feature: Audiences, Data Management
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 32%

---

# 管理和自定义列表{#manage-and-customize-lists}



您可以使用资源管理器访问Campaign数据库中的记录列表。 您可以筛选这些列表、运行搜索、添加信息、筛选和排序数据。

## 对记录计数 {#counting-records}

默认情况下，Adobe Campaign会加载列表的前200条记录。 这意味着显示不一定显示您正在查看的表的所有记录。 您可以统计列表中的记录数量并加载更多记录。

在列表屏幕的右下角， **[!UICONTROL counter]** 显示已加载的记录数以及数据库中的记录总数（应用任何过滤器后）：

![](assets/s_ncs_user_nb_200_0.png)

如果&quot;**？**“”而不是右侧的数字，请单击计数器开始计算。

### 加载更多记录 {#loading-more-records}

要加载（并因此显示）附加记录（默认为200行），请单击 **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

要加载所有记录，请右键单击列表并选择 **[!UICONTROL Load all]**.

>[!CAUTION]
>
>根据记录数，加载完整列表的时间可能会很长。

### 更改默认的记录数 {#change-default-number-of-records}

要更改加载的默认记录数，请单击 **[!UICONTROL Configure list]** 在列表的右下角。

![](assets/s_ncs_user_configure_list.png)

在列表配置窗口中，单击 **[!UICONTROL Advanced parameters]** （左下方）并更改要检索的行数。

![](assets/s_ncs_user_configurelist_advancedparam.png)

## 配置列表 {#configuring-lists}

### 添加列 {#add-columns}

在列表中添加列有两种方法。

您可以从记录的详细信息中快速向列表中添加列。 操作步骤：

1. 在详细信息屏幕中，右键单击要在列中显示的字段。
1. 选择 **[!UICONTROL Add in the list]**。

   该列会添加到现有列的右侧。

![](assets/s_ncs_user_add_in_list.png)

添加列的另一种方法（例如，如果要显示未在详细信息屏幕上显示的数据）是使用列表配置窗口。 操作步骤：

1. 单击 **[!UICONTROL Configure list]** 列表右下方。

   ![](assets/s_ncs_user_configure_list.png)

1. 在列表配置窗口中，双击要添加到 **[!UICONTROL Available fields]** 列表以将其添加到 **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >默认情况下，不显示高级字段。 要显示它们，请单击可用字段列表右下方的 **Display advanced fields**。
   >
   >会按照数据库表，然后按字母顺序显示各个标签。
   >
   >使用 **Search** 字段，以在可用字段中运行搜索。 欲知更多信息，请参见 [本节](#sorting-a-list).
   >
   >字段由特定图标标识：SQL字段、链接表、计算字段等。 对于每个选定的字段，描述都显示在可用字段列表下。 [了解详情](#configuring-lists)。
   >
   >您还可以对数据进行排序和过滤。 请参阅[此小节](../../platform/using/filtering-options.md)。

1. 对要显示的每个列重复此步骤。
1. 使用箭头修改 **显示顺序**. 值最高的列将显示在记录列表的左侧。

   ![](assets/s_ncs_user_columns_order_down.png)

1. 如果需要，您可以单击 **[!UICONTROL Distribution of values]** 查看当前文件夹中所选字段值的重新分区。

   ![](assets/s_ncs_user_configurelist_values.png)

1. 单击 **[!UICONTROL OK]** 以确认配置并显示结果。

### 新建列 {#create-a-new-column}

您可以创建新列以在列表中显示附加字段。 操作步骤：

1. 单击 **[!UICONTROL Configure the list]** 位于列表下方和右侧。
1. 单击 **[!UICONTROL Add]** 以在列表中显示新字段。

### 移除列 {#remove-a-column}

您可以使用对记录列表中的一列或多列进行掩码 **[!UICONTROL Configure list]** 位于列表右下方。

![](assets/s_ncs_user_configure_list.png)

在列表配置窗口中，选择要遮罩的列 **[!UICONTROL Output columns]** 区域，然后单击“删除”按钮。

![](assets/s_ncs_user_removecolumn_icon.png)

对要遮罩的每一列重复此操作。 单击 **[!UICONTROL OK]** 以确认配置并显示结果。

### 调整列宽 {#adjust-column-width}

当列表处于活动状态（即至少选择了一行）时，您可以使用F9调整列的宽度，以使所有列都可以在屏幕上显示。

### 在子文件夹中显示数据 {#display-sub-folders-records}

列表可显示：

* 仅包含在所选文件夹中的记录，
* 或是所选文件夹及其子文件夹中的记录。

要从一种显示模式切换到另一种显示模式，请单击 **[!UICONTROL Display sub-levels]** 工具栏中。

![](assets/s_ncs_user_display_children_icon.png)

## 保存列表配置 {#saving-a-list-configuration}

列表配置是在工作站级别本地定义的。 清空本地缓存时，本地配置被禁用。

默认情况下，定义的显示参数适用于具有相应文件夹类型的所有列表。 因此，当您从文件夹修改收件人列表显示方式时，这个配置将应用到所有其他收件人文件夹。

但是，可以保存多个要应用于相同类型的不同文件夹的配置。 该配置会随包含数据的文件夹的属性一同保存，并可重新应用。

例如，对于投放文件夹，可以配置以下显示：

![](assets/s_ncs_user_folder_save_config_1.png)

要保存此列表配置，使其可重复使用，可执行以下操作：

1. 右键单击其中包含已显示数据的文件夹。
1. 选择 **[!UICONTROL Properties]**。
1. 单击 **[!UICONTROL Advanced settings]** 然后在 **[!UICONTROL Configuration]** 字段。

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. 单击 **[!UICONTROL OK]** 然后单击 **[!UICONTROL Save]**.

然后可将此配置应用到另一个 **Delivery** 文件夹：

![](assets/s_ncs_user_folder_save_config_3.png)

单击 **[!UICONTROL Save]** 在文件夹属性窗口中。 此时会修改列表显示，以符合所指定的配置：

![](assets/s_ncs_user_folder_save_config_5.png)

## 导出列表 {#exporting-a-list}

要从列表中导出数据，必须使用导出向导。 要访问它，请从列表中选择要导出的元素，右键单击并选择 **[!UICONTROL Export...]**.

有关导入和导出功能的使用说明，请参见 [通用导入和导出](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>不得使用“复制/粘贴”功能从列表中导出元素。

## 对列表排序 {#sorting-a-list}

列表可能包含大量数据。 您可以对这些数据进行排序，或者应用简单或高级过滤器。 排序允许您按升序或降序显示数据。 您可以利用过滤器来定义并组合各种标准，从而仅显示所选的数据。

单击列标题可应用升序或降序排序，或取消数据排序。 活动排序状态和排序顺序在列标签之前用蓝色箭头指示。 列标签前面的红色短划线表示排序应用于从数据库索引的数据。 此排序方法用于优化排序作业。

您还可以配置排序或组合排序标准。 为此请执行以下操作步骤：

1. **[!UICONTROL Configure list]** 列表右下方。

   ![](assets/s_ncs_user_configure_list.png)

1. 在列表配置窗口中，单击 **[!UICONTROL Sorting]** 选项卡。
1. 选择要排序的字段以及排序方向（升序或降序）。

   ![](assets/s_ncs_user_configurelist_sort.png)

1. 排序优先级由排序列的顺序定义。 要改变优先级，可使用适当的图标改变各列的顺序。

   ![](assets/s_ncs_user_configurelist_move.png)

   排序优先级不会影响列表中各类的显示情况。

1. 单击 **[!UICONTROL Ok]** 以确认此配置并在列表中显示结果。

### 搜索元素 {#running-a-search}

您可以使用在编辑器中运行可用字段的搜索 **[!UICONTROL Search]** 字段列表上方的字段。 按 **输入** 在键盘上或浏览列表。 符合搜索内容的字段将以粗体标签显示。

>[!NOTE]
>
>您可以创建过滤器以仅显示列表中的某些数据。 [了解详情](../../platform/using/creating-filters.md)。
