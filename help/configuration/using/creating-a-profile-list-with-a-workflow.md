---
product: campaign
title: 使用工作流创建轮廓列表
description: 了解如何在工作流中创建用户档案列表
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
TQID: 'https://experienceleague.adobe.com/km2D2qnUAdgDCauLUYcWSC-J567twPEyvaZBsLDAOKA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 11%
---
# 使用工作流创建轮廓列表{#creating-a-profile-list-with-a-workflow}


要基于新的收件人表创建&#x200B;**[!UICONTROL List]**&#x200B;类型列表，您需要创建将生成该列表的定向工作流。

有关Campaign中列表的详细信息，请参阅[此部分](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

要在自定义收件人表中创建定位工作流并更新收件人，请执行以下步骤：

1. 转到资源管理器的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;节点。
1. 创建新的定位工作流。
1. 放置&#x200B;**查询**&#x200B;活动，然后放置&#x200B;**列表更新**&#x200B;活动。

   ![](assets/mapping_create_list_workflow01.png)

1. 双击&#x200B;**查询**&#x200B;活动，然后单击&#x200B;**[!UICONTROL Edit the query]**&#x200B;以根据新收件人表的架构选择定向维度（在我们的示例中：**个人**）。 单击 **[!UICONTROL Finish]** 确认。

   ![](assets/mapping_create_list_workflow03.png)

1. 双击&#x200B;**列表更新**&#x200B;活动，然后选择&#x200B;**[!UICONTROL Create the list if necessary (Computed name)]**&#x200B;单选按钮。

   ![](assets/mapping_create_list_workflow02.png)

1. 为新列表选择创建文件夹。
1. 执行工作流以创建列表。
1. 在&#x200B;**[!UICONTROL List update]**&#x200B;活动期间选择的树节点中查看结果。

   仪表板指定列表所基于的架构，如下所示：

   ![](assets/mapping_list_view.png)
