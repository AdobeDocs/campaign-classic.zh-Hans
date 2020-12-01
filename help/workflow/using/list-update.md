---
solution: Campaign Classic
product: campaign
title: 列表更新
description: 列表更新
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# 列表更新{#list-update}

列表 **更新** 活动将过渡中指定的人口存储在列表中。

![](assets/s_user_segmentation_update_group.png)

可以从现有组的列表中选择列表。

还可以使用和选项创 **[!UICONTROL Create the list if necessary (Computed name)]** 建 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 它。 这些选项允许您选择所选的标签以创建列表，然后选择保存该文件的文件夹。 还可以通过插入动态字段或脚本自动生成标签。 标签右侧的弹出菜单中提供不同的动态字段。

![](assets/s_user_segmentation_update_list_calc.png)

如果列表已存在，则收件人将添加到现有内容，除非选中该选 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 项。 在这种情况下，列表的内容会在更新之前删除。

如果希望已创建或更新的列表使用除收件人表之外的表，请选中该选 **[!UICONTROL Create or use a list with its own table]** 项。

要使用该选项，必须在Adobe Campaign实例中配置了相关的特定表。

通常，在列表中保存目标会标记工作流的结束。 因此，默认 **[!UICONTROL List update]** 情况下活动没有出站过渡。 选中该 **[!UICONTROL Generate an outbound transition]** 选项可添加一个。

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中从资源管理器创建列表收件人](#video)

## 示例：列表更新 {#example--list-update}

在以下示例中，列表更新活动遵循查询，该的目标男子30岁以上居住在法国。 列表最初将根据查询结果创建。 然后，每次从工作流中启动它时，都会更新它。 例如，它可以定期用于活动的目标促销优惠。

1. 在查询 **[!UICONTROL list update activity]** 之后直接添加一个，然后打开它进行编辑。

   有关在工作流中创建查询的详细信息，请参阅 [查询](../../workflow/using/query.md)。

1. 您可以为活动选择标签。
1. 选择选 **[!UICONTROL Create the list if necessary (Calculated name)]** 项以显示在执行第一个工作流后将创建列表，然后使用以下执行进行更新。
1. 选择要保存列表的文件夹。
1. 输入列表的标签。 您可以插入动态字段以自动从列表生成名称。 在此示例中，列表与查询同名，可轻松识别其内容。
1. 选中 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 此选项可删除与定位条件不匹配的收件人，并将新的列表插入该。
1. Also leave the **[!UICONTROL Create or use a list with its own table]** option checked.
1. Leave the **[!UICONTROL Generate an outbound transition]** option unchecked.
1. Click **[!UICONTROL Ok]** then start the workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   然后创建或更新匹配收件人的列表。

## 输入参数 {#input-parameters}

* tableName
* 模式

标识要保存在组中的人口。

## 输出参数 {#output-parameters}

* groupId:组标识符。

## 教程视频 {#video}

此视频演示如何从资源管理器创建列表收件人。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

此处提供其他Campaign Classic操作方 [法视频](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html)。
