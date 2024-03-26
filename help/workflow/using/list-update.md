---
product: campaign
title: 列表更新
description: 列表更新
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 3%

---

# 列表更新{#list-update}



A **列表更新** 活动会将过渡中指定的群体存储在收件人列表中。

![](assets/s_user_segmentation_update_group.png)

可以从现有组的列表中选择该列表。

也可以使用创建 **[!UICONTROL Create the list if necessary (Computed name)]** 和 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 选项。 这些选项允许您选择您选择的标签来创建列表，以及稍后在其中保存该列表的文件夹。 通过插入动态字段或脚本，还可以自动生成标签。 标签右侧的弹出菜单中提供了不同的动态字段。

![](assets/s_user_segmentation_update_list_calc.png)

如果该列表已存在，则将收件人添加到现有内容，除非您选中 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 选项。 在这种情况下，将在更新之前删除列表的内容。

如果您希望创建或更新的列表使用收件人表以外的表，请检查 **[!UICONTROL Create or use a list with its own table]** 选项。

要使用该选项，必须在您的Adobe Campaign实例中配置相关的特定表。

通常，将目标保存在列表中会标记工作流的结尾。 默认情况下， **[!UICONTROL List update]** 因此，活动没有叫客过渡。 查看 **[!UICONTROL Generate an outbound transition]** 选项以添加一个。

![](assets/do-not-localize/how-to-video.png) [在视频中了解如何从资源管理器创建收件人列表](#video)

## 示例：列表更新 {#example--list-update}

在以下示例中，列表更新活动遵循一个查询，该查询针对的是居住在法国的30岁以上的男性。 列表最初将根据查询结果创建。 然后，每次从工作流中启动它时都会更新它。 例如，它可以定期用于针对营销活动的定向促销选件。

1. 添加 **[!UICONTROL list update activity]** 紧跟查询之后，然后打开该查询以进行编辑。

   有关在工作流中创建查询的更多信息，请参阅 [查询](query.md).

1. 您可以为活动选择标签。
1. 选择 **[!UICONTROL Create the list if necessary (Calculated name)]** 选项，用于显示将在执行第一个工作流后创建列表，然后使用以下执行进行更新。
1. 选择要保存列表的文件夹。
1. 输入列表的标签。 您可以插入动态字段以从列表中自动生成名称。 在此示例中，列表与查询具有相同的名称，以便轻松识别其内容。
1. 离开 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 选中此选项可删除不符合定位标准的收件人，并将新收件人插入到列表中。
1. 另请保留 **[!UICONTROL Create or use a list with its own table]** 选项已选中。
1. 离开 **[!UICONTROL Generate an outbound transition]** 选项未选中。
1. 单击 **[!UICONTROL Ok]** 然后启动工作流。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   随后将创建或更新匹配的收件人列表。

## 输入参数 {#input-parameters}

* 表名
* 架构

标识要保存在组中的群体。

## 输出参数 {#output-parameters}

* groupId：组标识符。

## 教程视频 {#video}

本视频说明如何从资源管理器创建收件人列表。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
