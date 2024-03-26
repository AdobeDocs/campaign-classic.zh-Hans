---
title: 使用外部重复数据删除活动的合并功能
description: 了解如何使用重复数据删除活动的合并功能
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Data Management
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 6%

---

# 使用外部重复数据删除活动的合并功能 {#deduplication-merge}



## 关于此用例 {#about-this-use-case}

此用例描述了如何使用 **[!UICONTROL Merge]** 中的功能 **[!UICONTROL Deduplication]** 活动。

有关此功能的详细信息，请参阅 [本节](deduplication.md#merging-fields-into-single-record).

此 **[!UICONTROL Deduplication]** activity用于从数据集中删除重复行。 在此使用案例中，根据Email字段重复了以下显示的数据。

| 上次修改日期 | 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 罗伯特 | 提斯纳 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鲍比 | 提斯纳 | bob@mycompany.com | | 777-777-7777 |
| 10/03/2020 | 鲍勃 |  | bob@mycompany.com | | 888-888-8888 |

利用重复数据删除活动的 **[!UICONTROL Merge]** 通过功能，您可以为重复数据删除配置一组规则，以定义要合并到单个结果数据记录中的一组字段。 例如，如果有一组重复记录，则可以选择保留最早的电话号码或最近的名称。

## 激活合并功能 {#activating-merge}


要启用合并功能，您首先需要配置 **[!UICONTROL Deduplication]** 活动。 为此，请执行以下步骤：

1. 打开活动，然后单击 **[编辑配置]** 链接。

1. 选择要用于重复数据删除的协调字段，然后单击 **[!UICONTROL Next]**. 在本例中，我们要根据电子邮件字段删除重复项。

   ![](assets/uc_merge_edit.png)

1. 单击 **[!UICONTROL Advanced parameters]** 链接，然后激活 **[!UICONTROL Merge records]** 和 **[!UICONTROL Use several record merging criteria]** 选项。

   ![](assets/uc_merge_advanced_parameters.png)

1. 此 **[!UICONTROL Merge]** 选项卡将添加到 **[!UICONTROL Deduplication]** 配置屏幕。 我们将使用此选项卡指定在执行重复数据删除时要合并的数据。

## 配置要合并的字段 {#configuring-rules}

以下是我们要用于将数据合并到单个记录的规则：

* 保留最新名称（名字和姓氏字段），
* 保留最新的手机，
* 保留最旧的电话号码，
* 组中的所有字段都必须不为null才符合最终记录的条件。

要配置这些规则，请执行以下步骤：

1. 打开 **[!UICONTROL Merge]** 选项卡，然后单击 **[!UICONTROL Add]** 按钮。

   ![](assets/uc_merge_add.png)

1. 指定要合并的字段组的标识符和标签。

   ![](assets/uc_merge_identifier.png)

1. 指明选择要考虑的记录的条件。

   ![](assets/uc_merge_filter.png)

1. 对上次修改日期进行排序，以便选择最近名称。

   ![](assets/uc_merge_sort.png)

1. 选择要合并的字段。 在本例中，我们希望保留名字和姓氏字段。

   ![](assets/uc_merge_keep.png)

1. 这些字段将添加到要合并的数据集，并且新元素将添加到工作流架构。

   重复这些步骤以配置手机和电话字段。

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## 结果 {#results}

配置这些规则后，将在 **[!UICONTROL Deduplication]** 活动。

| 修改日期 | 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 罗伯特 | 提斯纳 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鲍比 | 提斯纳 | bob@mycompany.com | | 777-777-7777 |
| 10/03/2020 | 鲍勃 |  | bob@mycompany.com | | 888-888-8888 |

根据之前配置的规则，从这三条记录中合并结果。 经过比较，得出使用最新姓名、手机以及原始电话号码的结论。

| 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
|------------|-----------|-------|--------------|------|
| 鲍比 | 提斯纳 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> 请注意，已合并的名字是“Bobby”，因为我们已经配置了由名字和姓氏字段组成的“Name”规则。
>
>因此，无法考虑“Bob”（最近的名字），因为其关联的姓氏字段为空。 最新的名字和姓氏组合被合并到最终记录中。
