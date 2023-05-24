---
product: campaign
title: 配置投放
description: 了解如何通过专用用例执行A/B测试
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 在工作流中配置投放 {#step-4--configuring-the-deliveries-in-the-workflow}



一次 [创建群体](a-b-testing-uc-population-samples.md)，您可以配置投放。 在此使用案例中，前两个投放使您能够向群体A和B发送不同的内容。第三个投放是回退投放：将发送给不属于A或B的收件人。其内容将由脚本计算，并将与A或B相同，具体取决于哪个脚本的打开率最高。 我们需要为第三次投放配置一个等待期，以便了解投放A和B的结果。这就是为什么第三次投放包含 **[!UICONTROL Wait]** 活动。

1. 转到 **[!UICONTROL Split]** 活动，并将定向为群体A的过渡链接到工作流中已有的某个电子邮件投放。

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. 双击投放以将其打开。
1. 使用下拉列表，为投放A选择模板。

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. 单击 **[!UICONTROL Continue]** 查看投放，然后保存它。

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. 链接以下项的过渡 **[!UICONTROL Split]** 定向到人群B的活动以发送第二封电子邮件。

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. 打开投放并在投放B中选择模板，然后保存投放。

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. 将计划发送给剩余群体的过渡链接到 **[!UICONTROL Wait]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. 打开 **[!UICONTROL Wait]** 并配置一个5天的等待期。

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. 链接 **[!UICONTROL Wait]** 的活动 **[!UICONTROL JavaScript code]** 活动。

   ![](assets/use_case_abtesting_createdeliveries_008.png)

您现在可以创建脚本。 [了解详情](a-b-testing-uc-script.md)。
