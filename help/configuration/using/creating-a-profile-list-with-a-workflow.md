---
title: 使用工作流创建配置文件列表
seo-title: 使用工作流创建配置文件列表
description: 使用工作流创建配置文件列表
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# 使用工作流创建配置文件列表{#creating-a-profile-list-with-a-workflow}

要根据新 **[!UICONTROL List]** 收件人表创建类型列表，您需要创建一个将生成列表的定位工作流。 有关营销活动中列表的详细信息，请参阅 [此部分](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

1. 转到资 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 源管理器的节点。
1. 创建新的定位工作流。
1. 放置 **Query** 活动后跟 **List更新活动** 。

   ![](assets/mapping_create_list_workflow01.png)

1. 双击“ **Query** ”活动，然后单击 **[!UICONTROL Edit the query]** 以根据新收件人表的架构选择定位维(在我们的示例中： **个人**)。 Click **[!UICONTROL Finish]** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. 双击“列表 **更新** ”活动，然后选择单 **[!UICONTROL Create the list if necessary (Computed name)]** 选按钮。

   ![](assets/mapping_create_list_workflow02.png)

1. 为新列表选择创建文件夹。
1. 执行创建列表的工作流。
1. 在活动过程中选择的树节点中查看结 **[!UICONTROL List update]** 果。

   功能板指定列表所基于的架构，如下所示：

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>您还可以参阅创建 [收件人列表视频](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) 。

