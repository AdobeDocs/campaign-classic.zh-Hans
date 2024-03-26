---
product: campaign
title: 创建定位工作流
description: 了解如何通过专用用例执行A/B测试
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# AB测试：创建定位工作流 {#step-1--creating-a-targeting-workflow}

您需要在中创建工作流 **[!UICONTROL Targeting and Workflows]** 营销活动的选项卡。 它由一个 **[!UICONTROL Query]** 活动， a **[!UICONTROL Split]** 链接到两个的活动 **[!UICONTROL Email delivery]** 活动， a **[!UICONTROL Wait]** 活动， a **[!UICONTROL JavaScript code]** 活动和 **[!UICONTROL Delivery]** 活动。

1. 如果您尚未这样做，请创建一个营销活动(有关更多信息，请参阅 [本节](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 转到 **[!UICONTROL Targeting and Workflows]** 选项卡。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改现有工作流的标签或单击 **[!UICONTROL Add]** 要创建新密码(有关更多信息，请参阅 [本节](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用鼠标将活动拖放到工作流图中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** 选项卡)， a **[!UICONTROL Split]** (**[!UICONTROL Target]** tab)，两个 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** 选项卡)， a **[!UICONTROL Wait]** 活动(**[!UICONTROL Flow Control]** 选项卡)， a **[!UICONTROL JavaScript code]** 活动(**[!UICONTROL Actions]** 选项卡)，以及 **[!UICONTROL Delivery]** 活动(**[!UICONTROL Actions]** 选项卡)。

![](assets/use_case_abtesting_targetwkfl_004.png)

您现在可以配置群体示例。 [了解详情](a-b-testing-uc-population-samples.md)。
