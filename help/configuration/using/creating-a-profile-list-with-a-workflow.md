---
title: 使用工作流创建用户档案列表
description: 了解如何在工作流中创建用户档案列表
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 7%

---


# 使用工作流创建用户档案列表{#creating-a-profile-list-with-a-workflow}

要根据新 **[!UICONTROL List]** 的列表表创建类型收件人，您需要创建一个将生成列表的定位工作流。

有关活动中列表的详细信息，请参 [阅本节](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

要在自定义收件人表中创建定位工作流并更新收件人，请执行以下步骤：

1. 转到资 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 源管理器的节点。
1. 创建新的定位工作流。
1. 放置 **查询** 活动，后 **跟列表** 更新活动。

   ![](assets/mapping_create_list_workflow01.png)

1. 多次-单 **击查询** ，然后单击 **[!UICONTROL Edit the query]** 以根据新收件人表的模式选择活动(在我们的示例中： **个人**)。 Click **[!UICONTROL Finish]** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. 多次-单击 **列表更新** 活动，然后选择 **[!UICONTROL Create the list if necessary (Computed name)]** 单选按钮。

   ![](assets/mapping_create_list_workflow02.png)

1. 为新列表选择创建文件夹。
1. 执行工作流以创建列表。
1. 视图结果，在活动中选择树的节 **[!UICONTROL List update]** 点。

   仪表板指定列表所基于的模式，如下所示：

   ![](assets/mapping_list_view.png)


