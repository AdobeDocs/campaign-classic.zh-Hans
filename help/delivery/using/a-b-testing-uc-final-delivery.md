---
product: campaign
title: 定义最终投放
description: 了解如何通过专用用例执行A/B测试
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# 定义最终投放 {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

创建脚本以选择A/B测试入选者后，您可以定义最终投放的参数。

1. 连接 **[!UICONTROL JavaScript code]** 活动到其余 **[!UICONTROL Delivery]** 活动。
1. 打开 **[!UICONTROL Delivery]** 活动。
1. 取消选中 **[!UICONTROL Generate an outbound transition]** 选项以使用此活动完成工作流。
1. 将其他选项保留为其默认值。

   ![](assets/ab_test_final_delivery.png)

通过准备过渡中指定的投放(通过 **[!UICONTROL Javascript Code]** 活动)，则您随后将能够批准该请求并开始发送，如下一步中所述。

您现在可以启动工作流。 [了解详情](a-b-testing-uc-start-workflow.md)。
