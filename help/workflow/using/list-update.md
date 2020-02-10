---
title: 列表更新
seo-title: 列表更新
description: 列表更新
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 列表更新{#list-update}

列 **表更新** ，活动将过渡中指定的人群存储在收件人列表中。

![](assets/s_user_segmentation_update_group.png)

可以从现有用户组的列表中选择该列表。

还可以使用和选项创建 **[!UICONTROL Create the list if necessary (Computed name)]** 该 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 库。 这些选项允许您选择所选的标签以创建列表，然后再选择保存列表的文件夹。 还可以通过插入动态字段或脚本自动生成标签。 标签右侧的弹出菜单中提供不同的动态字段。

![](assets/s_user_segmentation_update_list_calc.png)

如果列表已存在，则收件人将添加到现有内容，除非选中该选 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 项。 在这种情况下，列表内容会在更新之前删除。

如果希望创建或更新的列表使用收件人表以外的表，请选中该选 **[!UICONTROL Create or use a list with its own table]** 项。

要使用此选项，必须在Adobe Campaign实例中配置了相关的特定表。

通常，将目标保存到列表中会标记工作流的结束。 因此，默认情 **[!UICONTROL List update]** 况下，活动没有出站过渡。 选中此 **[!UICONTROL Generate an outbound transition]** 选项可添加一个。

## 示例：列表更新 {#example--list-update}

在以下示例中，列表更新活动跟在一个查询之后，该查询以居住在法国的30岁以上男性为目标。 列表最初将根据查询结果创建。 然后，每次从工作流中启动它时，都会更新它。 例如，它可以定期用于营销活动的定向促销优惠。

1. 在查询 **[!UICONTROL list update activity]** 后直接添加一个，然后打开该查询进行编辑。

   有关在工作流中创建查询的详细信息，请参阅 [查询](../../workflow/using/query.md)。

1. 您可以为活动选择标签。
1. 选择 **[!UICONTROL Create the list if necessary (Calculated name)]** 此选项可显示在执行第一个工作流后将创建列表，然后使用以下执行进行更新。
1. 选择要保存列表的文件夹。
1. 输入列表的标签。 您可以插入动态字段以自动从列表中生成名称。 在此示例中，列表与查询同名，可轻松标识其内容。
1. 选中 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 此选项可删除与定位条件不匹配的收件人，并将新收件人插入列表。
1. 同时，将选 **[!UICONTROL Create or use a list with its own table]** 中此选项。
1. 不选中 **[!UICONTROL Generate an outbound transition]** 此选项。
1. 单击 **[!UICONTROL Ok]** 然后启动工作流。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   随后将创建或更新匹配收件人的列表。

有关此内容的详细信息，请参阅 [创建收件人列表视频](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 。

## 输入参数 {#input-parameters}

* tableName
* 架构

标识要保存在组中的人群。

## 输出参数 {#output-parameters}

* groupId

组标识符。
