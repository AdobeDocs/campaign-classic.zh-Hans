---
solution: Campaign Classic
product: campaign
title: 配置投放
description: 了解如何通过专用用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# 在工作流{#step-4--configuring-the-deliveries-in-the-workflow}中配置投放

下一步是配置投放。 它们的目标是前一阶段创造的三个人口：[步骤2:配置填充示例](#step-2--configuring-population-samples)。 前两个投放允许您向群体A和B发送不同的内容。第三个投放用于未接收A和B的群体。其内容将由脚本计算，并且与A或B相同，具体取决于打开率最高的群体。 我们需要为第三个投放配置等待期，以了解投放A和B的结果。这就是为什么第三个投放包括&#x200B;**[!UICONTROL Wait]**&#x200B;活动。

1. 转到&#x200B;**[!UICONTROL Split]**&#x200B;活动，将用于填充A的过渡链接到工作流中已有的电子邮件投放之一。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 多次-单击投放以打开它。
1. 使用下拉列表，选择投放A的模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 单击&#x200B;**[!UICONTROL Continue]**&#x200B;视图投放，然后保存它。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 将用于人口B的&#x200B;**[!UICONTROL Split]**&#x200B;活动的过渡链接到第二个电子邮件投放。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 打开投放，在投放B中选择模板，然后保存投放。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 将用于剩余人口的过渡链接到&#x200B;**[!UICONTROL Wait]**&#x200B;活动。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 打开&#x200B;**[!UICONTROL Wait]**&#x200B;活动并配置5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 将&#x200B;**[!UICONTROL Wait]**&#x200B;活动链接到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动。

   ![](assets/use_case_abtesting_createdeliveries_008.png)
