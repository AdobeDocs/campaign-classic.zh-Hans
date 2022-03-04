---
product: campaign
title: 配置投放
description: 了解如何通过专用用例执行A/B测试
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 在工作流中配置投放 {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

一次 [群体创建](a-b-testing-uc-population-samples.md)，则可以配置投放。 在此用例中，前两个投放允许您向群体A和B发送不同的内容。第三个投放是回退投放：它将发送给不属于A或B的收件人。其内容将由脚本计算，并且与A或B相同，具体取决于打开率最高的收件人。 我们需要为第三个投放配置一个等待期，以了解投放A和B的结果。这就是第三个投放包含的原因 **[!UICONTROL Wait]** 活动。

1. 转到 **[!UICONTROL Split]** 活动，并将定向于群体A的过渡链接到工作流中已有的电子邮件投放之一。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 双击投放以将其打开。
1. 使用下拉列表，选择投放A的模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 单击 **[!UICONTROL Continue]** 要查看投放，请保存它。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 链接的过渡 **[!UICONTROL Split]** 定向于群体B的活动，发送到第二个电子邮件投放。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 打开投放，在投放B中选择模板，然后保存投放。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 将发往剩余群体的过渡链接到 **[!UICONTROL Wait]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 打开 **[!UICONTROL Wait]** 活动，并配置5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 链接 **[!UICONTROL Wait]** 活动 **[!UICONTROL JavaScript code]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

您现在可以创建脚本。 [了解详情](a-b-testing-uc-script.md)。
