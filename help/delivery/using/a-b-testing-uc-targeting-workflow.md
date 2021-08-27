---
product: campaign
title: 创建定位工作流
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 创建定位工作流 {#step-1--creating-a-targeting-workflow}

![](../../assets/common.svg)

您需要在营销活动的&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;选项卡中创建工作流。 它由&#x200B;**[!UICONTROL Query]**&#x200B;活动、链接到两个&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动的&#x200B;**[!UICONTROL Split]**&#x200B;活动、**[!UICONTROL Wait]**&#x200B;活动、**[!UICONTROL JavaScript code]**&#x200B;活动和&#x200B;**[!UICONTROL Delivery]**&#x200B;活动组成。

1. 如果您尚未创建营销活动，请创建营销活动（有关更多信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 转到 **[!UICONTROL Targeting and Workflows]** 选项卡。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改现有工作流的标签或单击&#x200B;**[!UICONTROL Add]**&#x200B;以创建新工作流（有关更多信息，请参阅[此部分](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)）。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用鼠标将活动拖放到工作流图中，包括&#x200B;**[!UICONTROL Query]**（**[!UICONTROL Target]**&#x200B;选项卡）、**[!UICONTROL Split]**（**[!UICONTROL Target]**&#x200B;选项卡）、两个&#x200B;**[!UICONTROL Email deliveries]**（**[!UICONTROL Deliveries]**&#x200B;选项卡）、**[!UICONTROL Wait]**&#x200B;活动（**[!UICONTROL Flow Control]**&#x200B;选项卡）、**[!UICONTROL JavaScript code]**&#x200B;活动（**[!UICONTROL Actions]**&#x200B;选项卡）和&#x200B;**[!UICONTROL Delivery]**&#x200B;活动（**[!UICONTROL Actions]**&#x200B;选项卡）。

![](assets/use_case_abtesting_targetwkfl_004.png)

您现在可以配置群体样本。 [了解详情](a-b-testing-uc-population-samples.md)。
