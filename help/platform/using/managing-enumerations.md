---
solution: Campaign Classic
product: campaign
title: 管理明细列表
description: 管理明细列表
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# 管理明细列表{#managing-enumerations}

## 关于明细列表 {#about-enumerations}

明细列表(也称为“明细列表”)是系统建议用于填充某些字段的值列表。 明细列表允许您标准化这些字段的值，并帮助您输入数据或在查询中使用数据。

值的列表显示为下拉列表，您可以从中选择要在字段中输入的值。 下拉列表还支持预测输入，操作员输入前几个字母，应用程序填充其余字母。

某些控制台字段已用此类型的明细列表进行定义。 明细列表称为“open”（打开），如果您可以通过直接输入相应字段来添加值。

## 访问值 {#access-to-values}

定义此类型字段的值，并通过树的节点对这些字段进行整体管理(添加／删 **[!UICONTROL Administration > Platform > Enumerations]** 除值)。

![](assets/s_ncs_user_itemized_list_node.png)

* 上部分优惠一列表已定义明细列表的字段。
* 下部分列表建议的值。 这些值将在使用此字段的编辑器中重复。

   ![](assets/s_ncs_user_itemized_list_values.png)

   要创建新明细列表值，请单击 **[!UICONTROL Add]**。

   ![](assets/s_ncs_user_itemized_list.png)

   如果选 **[!UICONTROL Open]** 择了该选项，则用户可以直接在相应字段中添加新的逐项列表值。 通过确认消息可以创建此值。

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* 如果选 **[!UICONTROL Closed]** 择了该选项，则用户将无法创建新值，而只能从可用值中进行选择。

## 数据标准化 {#standardizing-data}

### 关于别名清理 {#about-alias-cleansing}

在明细列表字段中，您可以输入除明细列表值以外的值。 可以按原样存储，也可以清除。

>[!CAUTION]
>
>数据清理是影响数据库中数据的关键过程。 Adobe Campaign进行大量数据更新，这可能导致某些值被删除。 因此，此操作为专家用户保留。

输入值为：

* 已添加到明细列表值：在这种情况下，必 **[!UICONTROL Open]** 须选择该选项，
* 或自动替换为其相应别名：在这种情况下，必须在明细列表的 **[!UICONTROL Alias]** 选项卡中定义此情况，
* 或存储在别名列表中：稍后将为其分配别名。

   >[!NOTE]
   >
   >如果您需要使用清理功能，请在逐项 **[!UICONTROL Alias cleansing]** 列表中选择选项。

### 使用别名 {#using-aliases}

通过该 **[!UICONTROL Alias cleansing]** 选项，可以对选定的明细列表使用别名。 选择此选项后， **[!UICONTROL Alias]** 窗口底部将显示选项卡。

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### 创建别名 {#creating-an-alias}

要创建别名，请单击 **[!UICONTROL Add]**。

![](assets/s_ncs_user_itemized_list_alias_create.png)

输入要转换的别名和要应用的值，然后单击 **[!UICONTROL Ok]**。

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

在确认此操作之前检查参数。

>[!CAUTION]
>
>一旦此阶段被确认，以前输入的值可能无法恢复：他们被替换了。

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

因此，当用户在“公司” **字段** (在Adobe Campaign控制台或表单中)中输入值NEILSEN时，它将自动替换为值 **NIELSEN Ltd**。 值替换由别名清理 **工作流执行** 。 请参阅 [运行清理](#running-data-cleansing)。

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### 将值转换为别名 {#converting-values-into-aliases}

要将明细列表值转换为别名，请在值列表中右键单击，然后选择 **[!UICONTROL Convert values into aliases...]**。

![](assets/s_ncs_user_itemized_list_alias_detail.png)

选择要转换的值，然后单击 **[!UICONTROL Next]**。

![](assets/s_ncs_user_itemized_list_alias_transform.png)

单击 **[!UICONTROL Start]** 以运行转换。

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

执行完成后，别名将添加到别名列表。

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### 检索别名点击 {#retrieving-alias-hits}

用户输入的值可以转换为别名。 实际上，当用户输入一个未包含在项目化列表中的值时，该值会存储在选项卡 **[!UICONTROL Alias]** 中。

Alias **清理技术** 工作流每天晚上都会恢复这些值，以更新逐项列表。 请参阅运 [行数据清理](#running-data-cleansing)

如有必要， **[!UICONTROL Hits]** 该列可显示输入此值的次数。 计算此值既耗时又耗内存。 有关此问题的详细信息，请参 [阅计算条目出现](#calculating-entry-occurrences)。

### 运行数据清理 {#running-data-cleansing}

数据清理由技术工 **[!UICONTROL Alias cleansing]** 作流执行。 为明细列表定义的配置在执行过程中应用。 请参阅别 [名清理工作流](#alias-cleansing-workflow)。

清理可以通过链接 **[!UICONTROL Cleanse values...]** 触发。

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

通过 **[!UICONTROL Advanced parameters...]** 该链接，您可以设置开始将收集的值考虑在内的日期。

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

单击按 **[!UICONTROL Start]** 钮以运行数据清理。

#### 计算条目发生次数 {#calculating-entry-occurrences}

明 **[!UICONTROL Alias]** 细列表的子选项卡可以显示在输入的所有值中出现别名的次数。 此信息是估计值，将显示在列 **[!UICONTROL Hits]** 中。

>[!CAUTION]
>
>计算别名条目出现可能需要很长时间。 因此，在使用此函数时应谨慎。

您可以通过链接手动运行命中 **[!UICONTROL Cleanse values...]** 计算。 为此，请单击链 **[!UICONTROL Advanced parameters...]** 接并选择所需的选项。

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**:这允许您根据输入的日期更新已计算的命中数。
* **[!UICONTROL Recalculate the number of alias hits from the start]**:允许您在整个Adobe Campaign平台上运行计算。

您还可以创建专用工作流，以便计算在给定期间自动运行，例如每周运行一次。

为此，请创建工作流的副 **[!UICONTROL Alias cleansing]** 本，更改调度程序，并在活动中使用以下设 **[!UICONTROL Enumeration value cleansing]** 置：

* **-updateHits** ，用于更新别名点击数，
* **-updateHits:full** ，重新计算所有别名点击。

#### 别名清理工作流 {#alias-cleansing-workflow}

别名 **清理工作** 流运行明细列表值清理。 默认情况下，它每天执行。

它通过节点 **[!UICONTROL Administration > Production > Technical workflows]** 访问。

![](assets/s_ncs_user_itemized_list_alias_wf.png)

