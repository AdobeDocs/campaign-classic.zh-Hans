---
product: campaign
title: 创建定位工作流
description: 了解如何通过专用用例执行A/B测试
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# AB测试：创建定位工作流 {#step-1--creating-a-targeting-workflow}

您需要在营销策划的&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;选项卡中创建工作流。 它由一个&#x200B;**[!UICONTROL Query]**&#x200B;活动、链接到两个&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动的&#x200B;**[!UICONTROL Split]**&#x200B;活动、**[!UICONTROL Wait]**&#x200B;活动、**[!UICONTROL JavaScript code]**&#x200B;活动和&#x200B;**[!UICONTROL Delivery]**&#x200B;活动组成。

1. 如果您尚未这样做，请创建一个营销活动（有关更多信息，请参阅[此章节](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 转到&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;选项卡。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改现有工作流的标签或单击&#x200B;**[!UICONTROL Add]**&#x200B;以创建新工作流的标签（有关更多信息，请参阅[此章节](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)）。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用鼠标将活动拖放到工作流图中，包括&#x200B;**[!UICONTROL Query]** （**[!UICONTROL Target]**&#x200B;选项卡）、**[!UICONTROL Split]** （**[!UICONTROL Target]**&#x200B;选项卡）、两个&#x200B;**[!UICONTROL Email deliveries]** （**[!UICONTROL Deliveries]**&#x200B;选项卡）、**[!UICONTROL Wait]**&#x200B;活动（**[!UICONTROL Flow Control]**&#x200B;选项卡）、**[!UICONTROL JavaScript code]**&#x200B;活动（**[!UICONTROL Actions]**&#x200B;选项卡）和&#x200B;**[!UICONTROL Delivery]**&#x200B;活动（**[!UICONTROL Actions]**&#x200B;选项卡）。

![](assets/use_case_abtesting_targetwkfl_004.png)

您现在可以配置群体示例。 [了解详情](a-b-testing-uc-population-samples.md)。
