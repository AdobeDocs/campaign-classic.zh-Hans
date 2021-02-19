---
title: 使用外部重复数据删除活动的合并功能
description: 了解如何使用外部重复数据删除活动的合并功能
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 32a14eb99847dc04a582623204bc856c29fa4359
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 4%

---


# 使用外部重复数据删除活动的合并功能{#deduplication-merge}

## 关于此用例{#about-this-use-case}

此用例介绍如何使用&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动中的&#x200B;**[!UICONTROL Merge]**&#x200B;功能。

有关此字体的详细信息，请参阅[此部分](../../workflow/using/deduplication.md#merging-fields-into-single-record)。

**[!UICONTROL Deduplication]**&#x200B;活动用于从重复集中删除数据行。 在此用例中，下面显示的数据会根据“电子邮件”字段进行复制。

| 上次修改日期 | 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 罗伯特 | 蒂斯纳 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鲍比 | 蒂斯纳 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

使用外部重复数据删除活动的&#x200B;**[!UICONTROL Merge]**&#x200B;字体，您可以为外部重复数据删除配置一组规则，以定义一组字段，将其合并到单个生成的数据记录中。 例如，使用一组重复记录，您可以选择保留最旧的电话号码或最新的姓名。

## 激活合并功能{#activating-merge}


要启用合并功能，您首先需要配置&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动。 为此，请执行以下步骤：

1. 打开活动，然后单击&#x200B;**[编辑配置]**&#x200B;链接。

1. 选择要用于外部重复数据删除的对帐字段，然后单击&#x200B;**[!UICONTROL Next]**。 在此示例中，我们希望根据电子邮件字段进行重复数据消除。

   ![](assets/uc_merge_edit.png)

1. 单击&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接，然后激活&#x200B;**[!UICONTROL Merge records]**&#x200B;和&#x200B;**[!UICONTROL Use several record merging criteria]**&#x200B;选项。

   ![](assets/uc_merge_advanced_parameters.png)

1. **[!UICONTROL Merge]**&#x200B;选项卡将添加到&#x200B;**[!UICONTROL Deduplication]**&#x200B;配置屏幕。 我们将使用此选项卡指定执行外部重复数据删除时要合并的数据。

## 配置要合并{#configuring-rules}的字段

以下是我们希望使用的规则，将数据合并到单个记录中：

* 保留最新名称（名字和姓字段），
* 保留最新的手机，
* 保留最旧的电话号码，
* 组中的所有字段都必须为非空，才能符合最终记录的条件。

要配置这些规则，请执行以下步骤：

1. 打开&#x200B;**[!UICONTROL Merge]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

   ![](assets/uc_merge_add.png)

1. 指定要合并的字段组的标识符和标签。

   ![](assets/uc_merge_identifier.png)

1. 指示选择要考虑的记录的条件。

   ![](assets/uc_merge_filter.png)

1. 在上次修改日期排序，以选择最新名称。

   ![](assets/uc_merge_sort.png)

1. 选择要合并的字段。 在此示例中，我们希望保留名字和姓字段。

   ![](assets/uc_merge_keep.png)

1. 这些字段将添加到要合并的数据集，并且新元素将添加到工作流模式。

   重复这些步骤以配置移动电话和电话字段。

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## 结果{#results}

配置这些规则后，将在&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动结束时接收以下数据。

| 修改日期 | 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | 罗伯特 | 蒂斯纳 | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | 鲍比 | 蒂斯纳 | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

根据之前配置的规则，将结果从三个记录中合并。 经比较，得出使用最新名称和手机以及原始电话号码的结论。

| 名字 | 姓氏 | 电子邮件 | 手机 | 电话 |
|------------|-----------|-------|--------------|------|
| 鲍比 | 蒂斯纳 | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> 请注意，已合并的名是“Bobby”，因为我们配置了由名字和最后字段组成的“Name”规则。
>
>因此，无法考虑&quot;Bob&quot;（最近的名字），因为其关联的姓氏字段为空。 最近的名和姓组合被合并到最后记录中。
